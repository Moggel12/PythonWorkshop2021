Følgende er en måde at lave sten, saks, papir i Python. Jeg har valgt at gøre brug af mange af de ting i har lært for at i kan se èn måde at kombinere pensum indtil videre. Dette kan gøres på andre måder også, samtidigt med at det også godt kan gøres lidt mere simpelt. På denne måde for i også at se mere af hvordan man i virkeligheden inddeler sin kode i funktioner til at genbruge og til at øge læseligheden.
```Python
import random

# Sten saks papir

def sten_saks_papir():
    options = ["Sten", "Saks", "Papir"]
    wins = [0, 0, 0]
    rounds = 0
    sten_saks_papir_play(options, wins, rounds)

def sten_saks_papir_play(options, wins, rounds):
    while (True):
        player_choice = get_player_choice(options)
        computer_choice = get_computer_choice(options)
        winner = sten_saks_papir_winner(computer_choice, player_choice)
        update_wins(wins, winner)
        print_round(computer_choice, player_choice, wins, rounds, winner)
        rounds = rounds + 1

def get_player_choice(options):
    player_idx = int(input("Vælg én af følgende:\n1)Sten\n2)Saks\n3)Papir\n")) - 1
    return options[player_idx]

def get_computer_choice(options):
    computer_idx = random.randint(0,2)
    return options[computer_idx]

def print_round(computer_choice, player_choice, wins, rounds, winner):
    print("===================")
    print_stats(wins, rounds)
    print("------CHOICES------")
    print("Computer:", computer_choice)
    print("\tvs")
    print("Player:", player_choice)
    print("-------------------")
    print("WINNER:", winner)
    print("===================")
    print("\n")

def update_wins(wins, winner):
    if winner == "draw":
        wins[2] = wins[2] + 1
    elif winner == "pc":
        wins[0] = wins[0] + 1
    else:
        wins[1] = wins[1] + 1

def print_stats(wins, rounds):
    print("ROUND", rounds + 1)
    print("-------STATS-------")
    print("Computer:", wins[0])
    print("Player:", wins[1])
    print("Draws:", wins[2])

def sten_saks_papir_winner(choice_pc, choice_pl):
    if choice_pc == choice_pl:
        return "draw"
    elif (choice_pc == "Sten") and (choice_pl == "Saks"):
        return "pc"
    elif (choice_pc == "Saks") and (choice_pl == "Papir"):
        return "pc"
    elif (choice_pc == "Papir") and (choice_pl == "Sten"):
        return "pc"
    else:
        return "pl"

sten_saks_papir()
```
