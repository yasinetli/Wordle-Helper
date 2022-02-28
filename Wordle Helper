# wordle_helper.py
# Author : Yasin ETLİ
# Date created: 27/2/2022
# This script finds recommendations for the wordle game.

from data import list


# Calculate every letters' frequency in the original list

key_dict = {
    "a": 0, "b": 0, "c": 0, "d": 0, "e": 0, "f": 0, "g": 0, "h": 0, "i": 0, "j": 0, "k": 0, "l": 0, "m": 0, "n": 0,
    "o": 0, "p": 0, "q": 0, "r": 0, "s": 0, "t": 0, "u": 0, "v": 0, "w": 0, "x": 0, "y": 0, "z": 0
}

for word in list:
    for i in key_dict:
        letter_list = [word[0], word[1], word[2], word[3], word[4]]
        for letter in letter_list:
            if letter == i:
                key_dict[i] += 1

# Find the sum of the frequencies of the letters in each word in the original list.
# Then create a dictionary containing the words as keys and the total frequency value as values.
# Sort this created dictionary by values.

master_dict = {}
for word in list:
    letter_list_2 = []
    letter_score_2 = []
    letter_list_2.extend((word[0], word[1], word[2], word[3], word[4]))
    for letter in letter_list_2:
        score = key_dict.get(letter, 0)
        letter_score_2.append(score)
    master_dict[word] = sum(letter_score_2)

master = dict(sorted(master_dict.items(), key=lambda item: item[1]))

# Entering the words "arose" and "until" for the first two choices was found to be the
# best choice in here: https://github.com/yasinetli/find_best_wordle_word.py
# After entering the first two words as these two words or as another 2 words of your choice, the game indicates
# the letters you know correctly with colors. Those who know the game will understand this situation.
# Here, when correctly known and incorrectly known letters are entered as input, possible correct answers are
# selected from the word list and presented as a list.


def wordle_helper():
    contain_list = []
    while True:
        input_contain = input("Enter the letters that the true answer must contain. "
                              "When there is none remained type 'off' : ").lower()
        if input_contain == "off":
            break
        contain_list.append(input_contain)
    not_contain_list = []
    while True:
        input_not_contain = input("Enter the letters that the true answer must not contain. "
                                  "When there is none remained type 'off' : ").lower()
        if input_not_contain == "off":
            break
        not_contain_list.append(input_not_contain)

    print(contain_list)
    print(not_contain_list)
    third_word_dict = {}
    for words in master:
        let_list = []
        let_list.extend((words[0], words[1], words[2], words[3], words[4]))
        check_not_contain = any(item in let_list for item in not_contain_list)
        check_contain = all(item in let_list for item in contain_list)
        if check_not_contain is False and check_contain is True:
            third_word_dict[words] = master[words]

    print(third_word_dict)


wordle_helper()
