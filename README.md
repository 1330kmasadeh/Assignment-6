Assignment 6  
**Structured Scripts Using Functions**  
Khaled Masadeh  

---

## Question 1 – Namespace Identifier

Based on the `space_mission_simulator.py` example from lecture slide #22, the identifiers can be categorized as follows:

| Identifier Variable | Scope | Lifetime |
|---------------------|--------|----------|
| AGENCY_NAME | Module (Global) | Entire program execution |
| mission_name | Parameter | During function call |
| fuel_level | Local Variable | Inside function execution |
| launch_mission() | Method (Function) | Entire program execution |
| print() | Built-in Function | Provided by Python |

### Explanation

- Module variables are declared outside all functions.
- Parameters are passed into functions.
- Local variables exist only while a function runs.
- Methods are defined using `def`.
- Built-in functions are provided by Python (e.g., print, input, len).

---

## Question 2 – Text Analysis Program

This script calculates the Flesch Reading Ease Index using structured functions.

---

## Question 3 – Server Management Console

This script applies an event-driven approach using a `while True` loop and exits when the user selects option 4.




def count_sentences(text):
    sentences = text.count('.') + text.count('!') + text.count('?')
    return sentences


def count_words(text):
    words = text.split()
    return len(words)


def count_syllables(text):
    vowels = "aeiouAEIOU"
    syllable_count = 0
    words = text.split()

    for word in words:
        for letter in word:
            if letter in vowels:
                syllable_count += 1

    return syllable_count


def calculate_flesch_index(words, sentences, syllables):
    if words == 0 or sentences == 0:
        return 0

    index = 206.835 - (1.015 * (words / sentences)) \
            - (84.6 * (syllables / words))

    return index


def main():
    filename = input("Enter the filename: ")

    try:
        with open(filename, 'r') as file:
            text = file.read()

        sentences = count_sentences(text)
        words = count_words(text)
        syllables = count_syllables(text)

        index = calculate_flesch_index(words, sentences, syllables)

        print("\nText Analysis Result")
        print("---------------------")
        print("Sentences:", sentences)
        print("Words:", words)
        print("Syllables:", syllables)
        print("Flesch Index:", round(index, 2))

    except FileNotFoundError:
        print("Error: File not found.")


if __name__ == "__main__":
    main()





def start_server():
    print("Server started successfully.")


def stop_server():
    print("Server stopped successfully.")


def check_status():
    print("Server status: Running.")


def display_menu():
    print("\nServer Management Console")
    print("1. Start Server")
    print("2. Stop Server")
    print("3. Check Server Status")
    print("4. Exit")


def main():
    while True:
        display_menu()
        choice = input("Select an option (1-4): ")

        if choice == "1":
            start_server()

        elif choice == "2":
            stop_server()

        elif choice == "3":
            check_status()

        elif choice == "4":
            print("Exiting program...")
            break

        else:
            print("Invalid selection. Please try again.")


if __name__ == "__main__":
    main()
