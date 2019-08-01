---
title: 1901090022-MIT60001-ProblemSet2(Part1)
date: 2019-07-30
tags: ['Python', 'MIT', '学习打卡']
categories: 'MIT60001'
---

### 打卡记录
- 学号：1901090022
- 学习课程：[Introduction to Computer Science and Programming in Python](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/)
- 学习内容：[Problem Set 2 (ZIP)](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/assignments/ps2.zip)
- 打卡天数：D05

### Part 1 作业要求（简述）:
#### A. 游戏要求:
1. 程序必须从 words.txt 文件中随机挑选一个单词。hangman.py 文件中已经实现了加载单词列表 和 随机选择单词 的功能。
2. 用户一开始有6次机会
3. 游戏一开始，提示用户有单词中有多少个字母，提示用户的机会次数。
4. 程序需要判断用户还有哪些字母可以猜

#### B. 用户交互:
The game must be interactive and flow as follows:

1. 每次在用户猜测之前，你需要显示以下信息：
    a. 提示用户所剩的次数
    b. 还有哪些字母用户还没有猜测
2. 提示用户每次只能猜一个字母
3. 每次等用户输入后，需要告诉用户所输入的单词是否在单词中
4. 等用户输入后，你还需要显示结果，哪些才对哪些还没有猜到，使用下划线来标识没有猜到的字母位置。
5. 最后，输出(­­­­­)符号，用户区分每一轮游戏

#### C. 用户输入要求：
1. 你可以假设用户每次只输入一个字符，但用户也许会输入数字、特殊符号、字母，你的程序只接收小写字母
2. 如果用户输入了字母意外的内容，你需要告诉用户只能输入字母。每当用户输入非字母字符、或者已经输入过的字母，将会减少一次警告的机会，如果没有了警告机会，游戏就会结束。

可以灵活运用一下函数：
- str.isalpha('your string')
- str.lower('Your String')

#### D. 游戏规则
1. 初始【警告次数【为3
2. 如果用户输入了非字母的内容，【警告次数】减一；没有警告次数，游戏失败
3. 如果用户输入了已经输入过的内容，【警告次数】减一 ；
4. 辅音：如果用户输入了辅音字母，且没有猜中，【猜测机会】减1
5. 元音：如果用户输入的原因字母，没有猜过，且没有猜中，【猜测机会】减2

#### E. 游戏终止条件
1. 当用户猜对了所有字母 或者 次数消耗完时终止游戏
2. 次数消耗完并且没有完成字母，告诉用户结果并显示正确的字母。
3. 用户赢了的话，输出恭喜信息，并显示用户分数
4. Total score = guesses_remaining* number unique letters in secret_word（总分 = 剩余猜测次数 x 单词字母数（去重））

### 作业心得
- 学会 not in list 的写法

## 程序代码（完成三个基本辅助函数）
```python
# Problem Set 2, hangman.py
# Name: 
# Collaborators:
# Time spent:

# Hangman Game
# -----------------------------------
# Helper code
# You don't need to understand this helper code,
# but you will have to know how to use the functions
# (so be sure to read the docstrings!)
import random
import string

WORDLIST_FILENAME = "words.txt"


def load_words():
    """
    Returns a list of valid words. Words are strings of lowercase letters.
    
    Depending on the size of the word list, this function may
    take a while to finish.
    """
    print("Loading word list from file...")
    # inFile: file
    inFile = open(WORDLIST_FILENAME, 'r')
    # line: string
    line = inFile.readline()
    # wordlist: list of strings
    wordlist = line.split()
    print("  ", len(wordlist), "words loaded.")
    return wordlist



def choose_word(wordlist):
    """
    wordlist (list): list of words (strings)
    
    Returns a word from wordlist at random
    """
    return random.choice(wordlist)

# end of helper code

# -----------------------------------

# Load the list of words into the variable wordlist
# so that it can be accessed from anywhere in the program
wordlist = load_words()


def is_word_guessed(secret_word, letters_guessed):
    '''
    secret_word: string, the word the user is guessing; assumes all letters are
      lowercase; 用户需要猜的单词，假设所有字母都是小写
    letters_guessed: list (of letters), which letters have been guessed so far;
      assumes that all letters are lowercase; 用户已经猜过的字母列表
    returns: boolean, True if all the letters of secret_word are in letters_guessed;
      False otherwise; 如果 secret_word 的字母，都在 letters_guessed 中，返回 True，否则返回 False
    '''
    for letter in secret_word:
        if letter not in letters_guessed:
            return False
    return True

def get_guessed_word(secret_word, letters_guessed):
    '''
    secret_word: string, the word the user is guessing; 用户需要猜的单词
    letters_guessed: list (of letters), which letters have been guessed so far; 目前猜过的字母
    returns: string, comprised of letters, underscores (_), and spaces that represents
      which letters in secret_word have been guessed so far.
    '''
    res = ""
    for letter in secret_word:
        if letter not in letters_guessed:
            res += "_ "
        else:
            res += letter
    return res

def get_available_letters(letters_guessed):
    '''
    letters_guessed: list (of letters), which letters have been guessed so far; 目前猜过的字母
    returns: string (of letters), comprised of letters that represents which letters have not
      yet been guessed.
    '''
    res = ""
    for letter in string.ascii_lowercase:
        if letter not in letters_guessed:
            res += letter
    return res

def hangman(secret_word):
    '''
    secret_word: string, the secret word to guess.
    
    Starts up an interactive game of Hangman.
    
    * At the start of the game, let the user know how many 
      letters the secret_word contains and how many guesses s/he starts with.
      
    * The user should start with 6 guesses

    * Before each round, you should display to the user how many guesses
      s/he has left and the letters that the user has not yet guessed.
    
    * Ask the user to supply one guess per round. Remember to make
      sure that the user puts in a letter!
    
    * The user should receive feedback immediately after each guess 
      about whether their guess appears in the computer's word.

    * After each guess, you should display to the user the 
      partially guessed word so far.
    
    Follows the other limitations detailed in the problem write-up.
    '''
    # FILL IN YOUR CODE HERE AND DELETE "pass"
    pass



# When you've completed your hangman function, scroll down to the bottom
# of the file and uncomment the first two lines to test
#(hint: you might want to pick your own
# secret_word while you're doing your own testing)


# -----------------------------------



def match_with_gaps(my_word, other_word):
    '''
    my_word: string with _ characters, current guess of secret word
    other_word: string, regular English word
    returns: boolean, True if all the actual letters of my_word match the 
        corresponding letters of other_word, or the letter is the special symbol
        _ , and my_word and other_word are of the same length;
        False otherwise: 
    '''
    # FILL IN YOUR CODE HERE AND DELETE "pass"
    pass



def show_possible_matches(my_word):
    '''
    my_word: string with _ characters, current guess of secret word
    returns: nothing, but should print out every word in wordlist that matches my_word
             Keep in mind that in hangman when a letter is guessed, all the positions
             at which that letter occurs in the secret word are revealed.
             Therefore, the hidden letter(_ ) cannot be one of the letters in the word
             that has already been revealed.

    '''
    # FILL IN YOUR CODE HERE AND DELETE "pass"
    pass



def hangman_with_hints(secret_word):
    '''
    secret_word: string, the secret word to guess.
    
    Starts up an interactive game of Hangman.
    
    * At the start of the game, let the user know how many 
      letters the secret_word contains and how many guesses s/he starts with.
      
    * The user should start with 6 guesses
    
    * Before each round, you should display to the user how many guesses
      s/he has left and the letters that the user has not yet guessed.
    
    * Ask the user to supply one guess per round. Make sure to check that the user guesses a letter
      
    * The user should receive feedback immediately after each guess 
      about whether their guess appears in the computer's word.

    * After each guess, you should display to the user the 
      partially guessed word so far.
      
    * If the guess is the symbol *, print out all words in wordlist that
      matches the current guessed word. 
    
    Follows the other limitations detailed in the problem write-up.
    '''
    # FILL IN YOUR CODE HERE AND DELETE "pass"
    pass



# When you've completed your hangman_with_hint function, comment the two similar
# lines above that were used to run the hangman function, and then uncomment
# these two lines and run this file to test!
# Hint: You might want to pick your own secret_word while you're testing.


if __name__ == "__main__":
    # pass

    # To test part 2, comment out the pass line above and
    # uncomment the following two lines.
    
    secret_word = choose_word(wordlist)
    hangman(secret_word)

###############
    
    # To test part 3 re-comment out the above lines and 
    # uncomment the following two lines. 
    
    #secret_word = choose_word(wordlist)
    #hangman_with_hints(secret_word)

```