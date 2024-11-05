# Wordle Guessing Program

## Overview

This program is designed to interact with a Wordle-like API to guess a hidden word based on feedback from previous guesses. It systematically identifies present letters and confirms their positions to deduce the correct word.

## Features

- **Identify Present Letters**: Makes guesses to find out which letters are present in the target word.
- **Guessing Logic**: Utilizes a structured approach to fill in the current state of the guessed word based on API responses.
- **Validation**: Confirms the final guessed word with the API to ensure accuracy.

## Logic Breakdown

### 1. Identify Present Letters

The program starts by making guesses using each letter of the alphabet. For each guess, it checks the API response to see if the letter is marked as "present" or "correct". All identified letters are collected into a set to avoid duplicates.

### 2. Guessing the Word

- **Initialization**: The current state of the word is initialized with placeholders (e.g., underscores). A dictionary tracks confirmed positions of letters.
- **Making Guesses**: The program loops through each present letter, guessing a word consisting solely of that letter (e.g., "aaaaa", "bbbbb"). The API response updates the position dictionary with confirmed letters.

### 3. Filling Unconfirmed Positions

For any positions that remain unconfirmed, the program attempts to fill them with present letters. It generates new guesses by placing a letter in each unconfirmed position and checks the API response. Confirmed letters are then updated in both the current state and the position dictionary.

### 4. Final Word Validation

Once all positions are filled, the program constructs the final guessed word and validates it with the API. It ensures that the guessed word is confirmed as correct before concluding the process.

## Code Structure

- **`guess_word(api_url, guess, seed, size)`**: Sends a guess to the API and returns the JSON response.
- **`find_present_letters(api_url, seed, size)`**: Identifies which letters are present in the target word.
- **`guess_with_letter(api_url, letter, seed, size, current_state, position_dict)`**: Makes a guess using a specific letter, updating the current state and position dictionary.
- **`fill_unconfirmed_positions(api_url, present_letters, size, current_state, position_dict, seed)`**: Fills in positions that haven't been confirmed yet.
- **`main(api_url, seed, size)`**: Orchestrates the overall guessing process.

## Usage

1. Set the `api_url` to point to the Wordle-like API.
2. Define a `seed` for the random word generation.
3. Optionally, set the `word_size` to the length of the word.
4. Call the `main(api_url, seed, word_size)` function to start the guessing process.

## Performance

The program has been optimized to reduce the number of API calls, improving the overall speed of the guessing process. The current implementation has demonstrated significant performance improvements.

## Conclusion

This Wordle guessing program effectively utilizes systematic guessing and validation techniques to determine the hidden word based on API feedback. It is a robust solution for engaging with Wordle-like challenges programmatically.