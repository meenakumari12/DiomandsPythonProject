import colorama
from colorama import Fore
import random


class Banker:
    def _init_(self):
        pass

    def diamond_suit(self):
        suit = "\u2666"
        ranks = [2, 3, 4, 5, 6, 7, 8, 9, 10, 'J', 'Q', 'K', 'A']
        diamond_cards = []
        for rank in ranks:
            diamond_cards.append((suit, rank))
        return diamond_cards


class Players:
    def _init_(self, suit):
        self.suit = suit

    def create_suit(self):
        ranks = [2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
        cards = []
        for rank in ranks:
            cards.append((self.suit, rank))
        return cards


def shuffle(cards):
    random.shuffle(cards)
    return cards


def pop_cards(cards):
    return cards.pop()


def award_points(card):
    rank = card[1]
    numbers = numbers = [2, 3, 4, 5, 6, 7, 8, 9, 10]
    royals = ['J', 'Q', 'K']
    if rank in numbers:
        points = 3
    elif rank in royals:
        points = 10
    else:
        points = 20
    return points


def final_winner(p1, p2, p3):
    if p1 > p2:
        if p1 > p3:
            print(Fore.BLUE + "\n---WINNER IS---", player1)
        elif p1 < p3:
            print(Fore.BLUE + "\n---WINNER IS---", player3)
        else:
            print(Fore.BLUE + "\n---THE GAME IS TIE BETWEEN ",
                  player1, "AND", player3)
    elif p2 > p3:
        if p2 > p1:
            print(Fore.BLUE + "\n---WINNER IS---", player2)
        elif p2 < p1:
            print(Fore.BLUE + "\n---WINNER IS---", player1)
        else:
            print(Fore.BLUE + "\n---THE GAME IS TIE BETWEEN ",
                  player2, "AND", player1)

    elif p3 > p1:
        if p3 > p2:
            print(Fore.BLUE + "\n---WINNER IS---", player3)
        elif p3 < p2:
            print(Fore.BLUE + "\n---WINNER IS---", player2)
        else:
            print(Fore.BLUE + "\n---THE GAME IS TIE BETWEEN ",
                  player3, "AND", player2)

    else:
        print(Fore.BLUE + "\n---THE THREE PLAYERS SCORES EQUALLY---")
        print(Fore.BLUE + "\n---WINNERS ARE---", player1, player2, player3)


def player_scores():
    p1_score = 0
    p2_score = 0
    p3_score = 0

    for round in range(1, 14):
        print(Fore.LIGHTRED_EX + '\n ROUND - ', round)
        shuffle(diamonds_list)
        diamond_card = pop_cards(diamonds_list)
        print(Fore.GREEN + "DISPLAYED DIAMOND CARD : ", diamond_card)

        shuffle(player1_list1)
        shuffle(player2_list2)
        shuffle(player3_list3)

        card1 = pop_cards(player1_list1)
        card2 = pop_cards(player2_list2)
        card3 = pop_cards(player3_list3)

        print('\n', player1)
        input("Press any key to select your card : ")
        print("\n   %s card  : %s" % (player1, card1))
        print("\n", player2)
        input("Press any key to select your card : ")
        print("\n   %s card  : %s" % (player2, card2))
        print("\n", player3)
        input("Press any key to select your card : ")
        print("\n   %s card  : %s" % (player3, card3))
        input("\nPress ENTER to know the scores")

        points = award_points(diamond_card)

        player1_points = []
        player2_points = []
        player3_points = []
        winners = card1
        winner = card1[1]

        if winner < card2[1]:
            if card3[1] < card2[1]:
                winners = card2
                player2_points.append(points)
                print(Fore.BLACK + "\n------DIAMOND CARD WON BY------",
                      player2, winners)
                print(player2, Fore.BLACK + "Wins and get points", player2_points)

            elif card2[1] == card3[1]:
                winner1 = card2
                winner2 = card3
                player2_points.append(points//2)
                player3_points.append(points//2)
                print(Fore.BLACK + "\n------DIAMOND CARD WON BY------",
                      player2, winner1, player3, winner2)
                print(player2, Fore.BLACK + " and ", player3, Fore.BLACK + " Wins and get points",
                      player2_points, player3_points)

            else:
                winners = card3
                player3_points.append(points)
                print(Fore.BLACK + "\n------DIAMOND CARD WON BY------",
                      player3, winners)
                print(player3, Fore.BLACK + "Wins and get points", player3_points)

        elif winner < card3[1]:
            winners = card3
            player3_points.append(points)
            print(Fore.BLACK + "\n------DIAMOND CARD WON BY------", player3, winners)
            print(player3, Fore.BLACK + "Wins and get points", player3_points)

        elif winner == card2[1]:
            if card2[1] < card3[1]:
                winners = card3
                player3_points.append(points)
                print(Fore.BLACK + "\n------DIAMOND CARD WON BY------",
                      player3, winners)
                print(player3, Fore.BLACK + "Wins and get points", player3_points)

            winner1 = card1
            winner2 = card2
            player1_points.append(points // 2)
            player2_points.append(points // 2)

            print(Fore.BLACK + "\n------DIAMOND CARD WON BY------",
                  player1, winner1, player2, winner2)
            print(player1, Fore.BLACK + " and ", player2, Fore.BLACK + " Wins and get points",
                  player1_points, player2_points)

        elif winner == card3[1]:
            winner1 = card1
            winner2 = card3
            player1_points.append(points//2)
            player3_points.append(points//2)
            print(Fore.BLACK + "\n------DIAMOND CARD WON BY------",
                  player1, winner1, player3, winner2)
            print(player1, Fore.BLACK + " and ", player3, Fore.BLACK + " Wins and get points",
                  player1_points, player3_points)

        else:
            player1_points.append(points)
            print(Fore.BLACK + "\n------DIAMOND CARD WON BY------", player1, winners)
            print(player1, Fore.BLACK + "Wins and get points", player1_points)

        p1_score = p1_score + sum(player1_points)
        p2_score = p2_score + sum(player2_points)
        p3_score = p3_score + sum(player3_points)

        print(Fore.LIGHTGREEN_EX + "\nAFTER ROUND %d THE PLAYERS SCORES : \n%s : %d\n%s : %d\n%s : %d" % (
            round, player1, p1_score, player2, p2_score, player3, p3_score))
        key = input(
            "\nPress any key to enter next round or to stop enter \'exit\' : ")
        if key == 'exit':
            break

    final_winner(p1_score, p2_score, p3_score)


print(Fore.CYAN + "\n------WELCOME TO DIAMONDS CARD GAME------")
print(Fore.CYAN + "\n-------PLAYER DETAILS-------\n")
player1 = (Fore.MAGENTA + str(input("ENTER PLAYER 1 NAME : ")))
player2 = (Fore.MAGENTA + str(input("ENTER PLAYER 2 NAME : ")))
player3 = (Fore.MAGENTA + str(input("ENTER PLAYER 3 NAME : ")))


banker = Banker()
diamonds_list = banker.diamond_suit()

player_1 = Players("\u2660")
player1_list1 = player_1.create_suit()

player_2 = Players("\u2665")
player2_list2 = player_2.create_suit()

player_3 = Players("\u2663")
player3_list3 = player_3.create_suit()

player_scores()


while (True):
    res = input("\nDO YOU WANT TO PLAY THIS GAME AGAIN yes/no : ")

    if res == 'yes':
        print(Fore.YELLOW+"\n*WELCOME TO DIAMONDS CARD GAME*")
        print(Fore.CYAN+"\n       PLAYER  DETAILS\n")
        player1 = (Fore.LIGHTBLUE_EX + str(input("ENTER PLAYER 1 NAME : ")))
        player2 = (Fore.LIGHTBLUE_EX + str(input("ENTER PLAYER 2 NAME : ")))
        player3 = (Fore.LIGHTBLUE_EX + str(input("ENTER PLAYER 3 NAME : ")))

        banker = Banker()
        diamonds_list = banker.diamond_suit()

        player_1 = Players("\u2660")
        player1_list1 = player_1.create_suit()

        player_2 = Players("\u2665")
        player2_list2 = player_2.create_suit()

        player_3 = Players("\u2663")
        player3_list3 = player_3.create_suit()

        player_scores()

    else:
        break