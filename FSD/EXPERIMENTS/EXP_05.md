# Lab Cycle - Experiment 5

## Aim:

Create a JavaScript program where a random number between 1 and 100 is generated
and the user is prompted to guess the number. Provide feedback on whether the guess
is too high, too low, or correct, and allow the user to keep guessing until they get it
right. After a correct guess, ask if they want to play again using confirm(); if yes,
restart the game, otherwise, display "Thanks for playing!" and end the program.
---

## html, js Code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prompt as alert</title>
</head>
<body>
    <h2>Guess the game Lab programm </h2>

        <script>
            function playGame() {
                const randomNumber = Math.floor(Math.random() * 100) + 1;
                let guess;
                let attempts = 0;
                while (true) {
                    guess = prompt("Guess a number between 1 and 100:");
                    if (guess === null) {
                        alert("Game cancelled.");
                        return;
                    }
                    guess = Number(guess);
                    if (isNaN(guess) || guess < 1 || guess > 100) {
                        alert("Please enter a valid number between 1 and 100.");
                        continue;
                    }
                    attempts++;
                    if (guess < randomNumber) {
                        alert("Too low! Try again.");
                    } else if (guess > randomNumber) {
                        alert("Too high! Try again.");
                    } else {
                        alert("Congratulations! You guessed the correct number: " + randomNumber + " in " + attempts + " attempts.");
                        break;
                    }
                }
                if (confirm("Do you want to play again?")) {
                    playGame();
                } else {
                    alert("Thanks for playing!");
                }
            }
            playGame();
        </script>
</body>
</html>
```

---
