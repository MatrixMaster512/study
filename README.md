# study
bot
class CaesarCipher:
    def __init__(self, shift):
        self.shift = shift
        self.alphabet = 'abcdefghijklmnopqrstuvwxyz'
        self.alphabet_upper = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'

    def encrypt(self, text):
        encrypted_text = ''
        for char in text:
            if char in self.alphabet:
                index = (self.alphabet.index(char) + self.shift) % 26
                encrypted_text += self.alphabet[index]
            elif char in self.alphabet_upper:
                index = (self.alphabet_upper.index(char) + self.shift) % 26
                encrypted_text += self.alphabet_upper[index]
            else:
                encrypted_text += char
        return encrypted_text

    def decrypt(self, text):
        decrypted_text = ''
        for char in text:
            if char in self.alphabet:
                index = (self.alphabet.index(char) - self.shift) % 26
                decrypted_text += self.alphabet[index]
            elif char in self.alphabet_upper:
                index = (self.alphabet_upper.index(char) - self.shift) % 26
                decrypted_text += self.alphabet_upper[index]
            else:
                decrypted_text += char
        return decrypted_text

def main():
    shift = int(input("Enter the shift value for Caesar Cipher: "))
    cipher = CaesarCipher(shift)

    while True:
        print("\nCaesar Cipher Menu")
        print("1. Encrypt text")
        print("2. Decrypt text")
        print("3. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            text = input("Enter the text to encrypt: ")
            encrypted_text = cipher.encrypt(text)
            print(f"Encrypted text: {encrypted_text}")
        elif choice == "2":
            text = input("Enter the text to decrypt: ")
            decrypted_text = cipher.decrypt(text)
            print(f"Decrypted text: {decrypted_text}")
        elif choice == "3":
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
