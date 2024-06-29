
#!/bin/bash

# Function to count files in current directory
file_count() {
    local files=$(ls -1 | wc -l)
    echo $files
}

# Main game logic
echo "Welcome to the Guessing Game!"

actual=$(file_count)

while true; do
    echo "Guess how many files are in the current directory:"
    read guess

    if [[ $guess -lt $actual ]]; then
        echo "Your guess is too low. Try again."
    elif [[ $guess -gt $actual ]]; then
        echo "Your guess is too high. Try again."
    else
        echo "Congratulations! You guessed correctly."
        break
    fi
done

exit 0

README.md: guessinggame.sh
    echo "# Guessing Game Project" > README.md
    echo "" >> README.md
    echo "This project was generated on:" >> README.md
    date >> README.md
    echo "" >> README.md
    echo "The number of lines in guessinggame.sh is:" >> README.md
    wc -l guessinggame.sh | egrep -o "[0-9]+" >> README.md
