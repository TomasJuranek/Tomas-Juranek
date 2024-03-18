"""
projekt_1.py: první projekt do Engeto Online Python Akademie

author: Tomáš Juránek   
email: juranek.t@gmail.com
discord: Tomas Ju
"""
'''
author =
'''
TEXTS = ['''
Situated about 10 miles west of Kemmerer,
Fossil Butte is a ruggedly impressive
topographic feature that rises sharply
some 1000 feet above Twin Creek Valley
to an elevation of more than 7500 feet
above sea level. The butte is located just
north of US 30N and the Union Pacific Railroad,
which traverse the valley. ''',
 '''At the base of Fossil Butte are the bright
red, purple, yellow and gray beds of the Wasatch
Formation. Eroded portions of these horizontal
beds slope gradually upward from the valley floor
and steepen abruptly. Overlying them and extending
to the top of the butte are the much steeper
buff-to-white beds of the Green River Formation,
which are about 300 feet thick.''',
'''The monument contains 8198 acres and protects
a portion of the largest deposit of freshwater fish
fossils in the world. The richest fossil fish deposits
are found in multiple limestone layers, which lie some
100 feet below the top of the butte. The fossils
represent several varieties of perch, as well as
other freshwater genera and herring similar to those
in modern oceans. Other fish such as paddlefish,
garpike and stingray are also present.'''
]

#Registrovaných uživatelů
uzivatel = {
            'bob' : '123',
            'ann' : 'pass123',
            'mike' : 'password123',
            'liz' : 'pass123'
}

# Vyžádaní přihlašovacích údajů od uživatele
username = input("username:")
password = input("password:")

# Ověření uživatelských údajů
if username in uzivatel and uzivatel[username] == password:
    print("$ python projekt1.py")
    print(f"Welcome to the app, {username}")
    print("We have 3 texts to be analyzed.")


# Výběr textu pro analýzu
    while True:
            text_choice = int(input("Enter a number btw. 1 and 3 to select:"))
            if text_choice not in range (1,4):
                print("Out of the range, please enter a number btw. 1 and 3")
                continue
            break
    
    # Získání vybraného textu
    selected_text = TEXTS[text_choice - 1]

    # Rozdělení textu na slova
    words = selected_text.split()

    # Inicializace proměnných pro statistiky
    num_words = len(words)
    num_titlecase = 0
    num_uppercase = 0
    num_lowercase = 0
    num_numbers = 0
    sum_numbers = 0
    word_lengths = {}
    
    # Pro každé slovo ve vybraném textu
    for word in words:
        # Kontrola počtu slov začínajících velkým písmenem
        if word.istitle():
            num_titlecase += 1
        # Kontrola počtu slov psaných velkými písmeny
        if word.isupper():
            num_uppercase += 1
        # Kontrola počtu slov psaných malými písmeny
        if word.islower():
            num_lowercase += 1
        # Kontrola počtu čísel
        if word.isdigit():
            num_numbers += 1
            sum_numbers += int(word)
        
        length = len(word)
        if length in word_lengths:
            word_lengths[length] += 1
        else:
            word_lengths[length] = 1
        

    # Výpis statistik
    print("\nStatistiky textu:")
    print(f"There are {num_words} words in the selected text.")
    print(f"There are {num_titlecase} titlecase words.")
    print(f"There are {num_uppercase} uppercase words.")
    print(f"There are {num_lowercase} lowercase words.")
    print(f"Thera are {num_numbers} numeric strings.")
    print(f"The sum of all the numbers {sum_numbers}")
    print("----------------------------------------")
    print("LEN|  OCCURENCES  |NR.")
    print("----------------------------------------")
    for length, occurrence in sorted(word_lengths.items()):
        print(f"{length:2}| {'*' * occurrence:14}| {occurrence}")
        
# Uživatel není registrovaná
else:
    print("$ python projekt1.py")
    print(f"username:{username}")
    print(f"password:{password}")
    print("unregistered user, terminating the program..")
