# PicoCTF Binary Search Game Solution

## Challenge Description

Welcome to the Binary Search Game! The objective is to guess a number between 1 and 1000 based on feedback provided after each guess.

## Manual Approach to Solve the Challenge

The challenge was solved using a manual binary search technique. Here's how the process went:

1. **Initial Guess:**
   - Guessed the midpoint of the range (1 to 1000):
     - Input: `500`
     - Response: `Higher! Try again.`

2. **Narrowing the Range:**
   - Next guess: `(500 + 1000) / 2 = 750`
     - Response: `Higher! Try again.`
   - Next guess: `(750 + 1000) / 2 = 875`
     - Response: `Lower! Try again.`
   - Next guess: `(750 + 875) / 2 = 812`
     - Response: `Lower! Try again.`
   - Next guess: `(750 + 812) / 2 = 781`
     - Response: `Higher! Try again.`
   - Next guess: `(781 + 812) / 2 = 796`
     - Response: `Higher! Try again.`
   - Next guess: `(796 + 812) / 2 = 804`
     - Response: `Higher! Try again.`
   - Next guess: `(804 + 812) / 2 = 808`
     - Response: `Higher! Try again.`
   - Next guess: `(808 + 812) / 2 = 810`
     - Response: `Congratulations! You guessed the correct number: 810`

3. **Flag Retrieved:**
   - The final output provided the flag:
     - `picoCTF{g00d_gu355_2e90d29b}`
