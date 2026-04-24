# Amo
import hashlib
import os
import base64
import secrets
from typing import Tuple, Optional
from cryptography.fernet import Fernet
from cryptography.hazmat.primitives import hashes
from cryptography.hazmat.primitives.kdf.pbkdf2 import PBKDF2
import bcrypt
import json
from datetime import datetime, timedelta

class PasswordEncryptionSystem:
    """
    A comprehensive password encryption system using modern cryptographic practices.
    Uses bcrypt for one-way password hashing and Fernet (AES) for reversible encryption.
    """
    
    def __init__(self, master_key: Optional[str] = None):
        """
        Initialize the encryption system.
        
        Args:
            master_key: Optional master key for reversible encryption
        """
        self.master_key = master_key
        self._fernet = None
        
        if master_key:
            self._initialize_fernet(master_key)
    
    def _initialize_fernet(self, master_key: str) -> None:
        """
        Initialize Fernet encryption with a master key.
        
        Args:
            master_key: Master key derived from user password
        """
        # Use PBKDF2 to derive a secure key from the master password
        salt = b'password_encryption_system_salt'  # In production, use a unique salt per user
        kdf = PBKDF2(
            algorithm=hashes.SHA256(),
            length=32,
            salt=salt,
            iterations=480000,
        )
        key = base64.urlsafe_b64encode(kdf.derive(master_key.encode()))
        self._fernet = Fernet(key)
    
    # ==================== ONE-WAY HASHING (for password storage) ====================
    
    def hash_password(self, password: str) -> str:
        """
        Hash a password using bcrypt for secure storage.
        This is a one-way operation - cannot be reversed.
        
        Args:
            password: Plain text password
            
        Returns:
            Hashed password string
        """
        # Generate a salt and hash the password
        salt = bcrypt.gensalt(rounds=12)  # 12 rounds is a good balance of security and speed
        hashed = bcrypt.hashpw(password.encode('utf-8'), salt)
        return hashed.decode('utf-8')
    
    def verify_password(self, password: str, hashed_password: str) -> bool:
        """
        Verify a password against its bcrypt hash.
        
        Args:
            password: Plain text password to check
            hashed_password: Previously hashed password
            
        Returns:
            True if password matches, False otherwise
        """
        try:
            return bcrypt.checkpw(
                password.encode('utf-8'),
                hashed_password.encode('utf-8')
            )
        except Exception:
            return False
    
    # ==================== REVERSIBLE ENCRYPTION ====================
    
    def encrypt_data(self, plaintext: str) -> Optional[str]:
        """
        Encrypt sensitive data using Fernet (AES-128 in CBC mode with PKCS7 padding).
        Requires a master key to be set.
        
        Args:
            plaintext: Data to encrypt
            
        Returns:
            Encrypted data as base64 string, or None if no master key set
        """
        if not self._fernet:
            raise ValueError("Master key not set. Cannot perform reversible encryption.")
        
        encrypted = self._fernet.encrypt(plaintext.encode('utf-8'))
        return encrypted.decode('utf-8')
    
    def decrypt_data(self, encrypted_data: str) -> Optional[str]:
        """
        Decrypt data that was encrypted with encrypt_data.
        Requires the same master key used for encryption.
        
        Args:
            encrypted_data: Encrypted data as base64 string
            
        Returns:
            Decrypted plaintext, or None if no master key set
        """
        if not self._fernet:
            raise ValueError("Master key not set. Cannot perform decryption.")
        
        try:
            decrypted = self._fernet.decrypt(encrypted_data.encode('utf-8'))
            return decrypted.decode('utf-8')
        except Exception:
            return None
    
    # ==================== PASSWORD STRENGTH CHECKING ====================
    
    @staticmethod
    def check_password_strength(password: str) -> Tuple[int, str]:
        """
        Evaluate the strength of a password.
        
        Args:
            password: Password to evaluate
            
        Returns:
            Tuple of (score 0-5, description)
        """
        score = 0
        feedback = []
        
        # Length check
        if len(password) >= 12:
            score += 2
        elif len(password) >= 8:
            score += 1
            feedback.append("Consider using a longer password (12+ characters)")
        else:
            feedback.append("Password is too short (minimum 8 characters)")
        
        # Complexity checks
        checks = {
            'uppercase': any(c.isupper() for c in password),
            'lowercase': any(c.islower() for c in password),
            'digits': any(c.isdigit() for c in password),
            'special': any(not c.isalnum() for c in password)
        }
        
        complexity_score = sum(checks.values())
        score += complexity_score // 2
        
        if complexity_score < 3:
            feedback.append("Use a mix of uppercase, lowercase, numbers, and special characters")
        
        # Common patterns check
        common_patterns = ['123', 'abc', 'qwerty', 'password', 'admin', 'letmein']
        if any(pattern in password.lower() for pattern in common_patterns):
            score = max(0, score - 2)
            feedback.append("Avoid common patterns and dictionary words")
        
        # Determine strength description
        if score >= 5:
            description = "Very Strong"
        elif score >= 4:
            description = "Strong"
        elif score >= 3:
            description = "Moderate"
        elif score >= 2:
            description = "Weak"
        else:
            description = "Very Weak"
        
        return score, description + (": " + "; ".join(feedback) if feedback else "")
    
    # ==================== SECURE PASSWORD GENERATION ====================
    
    @staticmethod
    def generate_secure_password(length: int = 16) -> str:
        """
        Generate a cryptographically secure random password.
        
        Args:
            length: Length of password (default 16)
            
        Returns:
            Secure random password string
        """
        alphabet = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+-=[]{}|;:,.<>?"
        
        while True:
            password = ''.join(secrets.choice(alphabet) for _ in range(length))
            
            # Ensure password meets minimum complexity requirements
            if (any(c.islower() for c in password) and
                any(c.isupper() for c in password) and
                any(c.isdigit() for c in password) and
                any(c in "!@#$%^&*()_+-=[]{}|;:,.<>?" for c in password)):
                return password
    
    # ==================== PASSWORD HISTORY MANAGEMENT ====================
    
    def create_password_history(self, password: str, max_history: int = 5) -> list:
        """
        Create a password history list to prevent password reuse.
        
        Args:
            password: Current password to add
            max_history: Maximum number of previous passwords to keep
            
        Returns:
            List of hashed previous passwords
        """
        history = []
        hashed_password = self.hash_password(password)
        history.append({
            'hash': hashed_password,
            'timestamp': datetime.now().isoformat()
        })
        return history[-max_history:]
    
    def is_password_reused(self, new_password: str, password_history: list) -> bool:
        """
        Check if a password has been used before.
        
        Args:
            new_password: New password to check
            password_history: List of previous password hashes
            
        Returns:
            True if password was used before, False otherwise
        """
        for entry in password_history:
            if self.verify_password(new_password, entry['hash']):
                return True
        return False


# ==================== USAGE EXAMPLES ====================

def demo_password_system():
    """Demonstrate the password encryption system functionality."""
    
    print("=" * 60)
    print("PASSWORD ENCRYPTION SYSTEM DEMO")
    print("=" * 60)
    
    # Initialize the system
    system = PasswordEncryptionSystem(master_key="my_secret_master_key")
    
    # Example 1: Password Hashing (One-way)
    print("\n1. PASSWORD HASHING (One-way)")
    print("-" * 40)
    
    password = "MySecureP@ssw0rd123"
    hashed = system.hash_password(password)
    print(f"Original: {password}")
    print(f"Hashed:   {hashed}")
    
    # Verify password
    is_valid = system.verify_password(password, hashed)
    print(f"Verification: {'✓ Valid' if is_valid else '✗ Invalid'}")
    
    # Try wrong password
    is_valid = system.verify_password("WrongPassword", hashed)
    print(f"Wrong password test: {'✓ Valid' if is_valid else '✗ Invalid'}")
    
    # Example 2: Password Strength Checking
    print("\n2. PASSWORD STRENGTH CHECKING")
    print("-" * 40)
    
    test_passwords = [
        "123",
        "password123",
        "MyPassword123",
        "MyP@ssw0rd!2024Secure"
    ]
    
    for pwd in test_passwords:
        score, description = system.check_password_strength(pwd)
        print(f"Password: {pwd:30} Score: {score}/5 - {description}")
    
    # Example 3: Secure Password Generation
    print("\n3. SECURE PASSWORD GENERATION")
    print("-" * 40)
    
    for i in range(3):
        generated = system.generate_secure_password(16)
        score, desc = system.check_password_strength(generated)
        print(f"Generated: {generated} (Strength: {score}/5)")
    
    # Example 4: Reversible Encryption
    print("\n4. REVERSIBLE ENCRYPTION")
    print("-" * 40)
    
    sensitive_data = "API_KEY=abc123xyz789"
    encrypted = system.encrypt_data(sensitive_data)
    print(f"Original:  {sensitive_data}")
    print(f"Encrypted: {encrypted}")
    
    decrypted = system.decrypt_data(encrypted)
    print(f"Decrypted: {decrypted}")
    
    # Example 5: Password History
    print("\n5. PASSWORD HISTORY MANAGEMENT")
    print("-" * 40)
    
    # Create password history
    old_passwords = ["OldPass1!", "OldPass2@", "OldPass3#"]
    history = []
    for old_pwd in old_passwords:
        history = system.create_password_history(old_pwd, max_history=5)
    
    # Check if new password was used before
    new_password = "OldPass2@"  # This one was used before
    is_reused = system.is_password_reused(new_password, history)
    print(f"Checking '{new_password}': {'✗ Already used!' if is_reused else '✓ New password'}")
    
    new_password = "BrandNewP@ss1"  # This is new
    is_reused = system.is_password_reused(new_password, history)
    print(f"Checking '{new_password}': {'✗ Already used!' if is_reused else '✓ New password'}")
    
    print("\n" + "=" * 60)
    print("Demo completed successfully!")
    print("=" * 60)


if __name__ == "__main__":
    # Install requirements first:
    # pip install bcrypt cryptography
    
    demo_password_system()
