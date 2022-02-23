# Bozhko_Elena_dz_11
Домашнее задание 


import random

number_pool = list(range(1, 91))
computer_card = random.sample(number_pool, 15)
computer_card_sorted = sorted(computer_card)
player_card = random.sample(number_pool, 15)
player_card_sorted = sorted(player_card)


def display_cards():
    print("Карточка компьютера:\n")
    print(computer_card_sorted)
    print("====================================")
    print("Карточка игрока:\n")
    print(player_card_sorted)


def lotto_choice():
    choice = random.choice(number_pool)
    number_pool.remove(choice)
    return choice


def the_game():
    while number_pool:
        choice = lotto_choice()
        print("Случайное число: " + str(choice))
        display_cards()
        cross_number = input("Вы хотите зачеркнуть число?")
        cross_number.lower()
        if cross_number == "Да":
            if choice in player_card_sorted:
                player_card_sorted.remove(choice)
            elif choice in computer_card_sorted:
                computer_card_sorted.remove(choice)
        if cross_number == "Нет":
            if choice in computer_card_sorted:
                computer_card_sorted.remove(choice)
            else:
                continue
    else:
        if len(player_card_sorted) == 0:
            print("Вы выиграли!")
        elif len(computer_card_sorted) == 0:
            print("Компьютер выиграл!")
        else:
            print("Игра закончилась")


the_game()
