# A2
A2 COP 4045

#Z23462050
#COP 4045
#method to encrypt a phrase
def encrypt(sentence, key):
    new_string = ""
    # for every character in the message
    for i in range(len(sentence)):
        #check if the character is lower case or upper
        if sentence[i].islower():
            #get position of character in alphabets
            character_num = ord(sentence[i]) - 97
            #get encrypted character
            new_char_num = (character_num+key)%26
            #add it to final string
            new_string += chr(new_char_num+97)
        else:
            character_num = ord(sentence[i]) - 65
            new_char_num = (character_num+key)%26
            new_string += chr(new_char_num+65)
    return new_string

#decrypt a message
def decrypt(sentence, key):
    new_string = ""
    for i in range(len(sentence)):
        if sentence[i].islower():
            character_num = ord(sentence[i]) - 97
            new_char_num = (character_num-key)%26
            new_string += chr(new_char_num+97)
        else:
            character_num = ord(sentence[i]) - 65
            new_char_num = (character_num-key)%26
            new_string += chr(new_char_num+65)
    return new_string

#main
def main():
    #show what to do
    print("This program is about Caesar's cipher")
    print("Enter the phrase you want and then the key will show to encrypt")
    print("Then enter if you want to do encryption or decryption")
    #loop
    while(True):
        #accept message, key and choice
        phrase = input("\nEnter the message: ")
        key = int(input("Enter the key: "))
        ed = input("Enter E for encryption, D for decryption: ")
        print("\nORIGINAL:  ", phrase)
        if ed == 'E':
            print("ENCRYPTED: ", encrypt(phrase, key))
        else:
            print("DECRYPTED: ", decrypt(phrase, key))
        
        #check if user wants to fo again
        choice = input("\nDo you want to try again? Y/N\t")
        if choice != 'Y':
            print("Goodbye\n")
            break

main()
