  
import java.util.Scanner;
import java.util.Random;
 
public class GuesstheNumber {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int totalScore = 0;
        int roundsPlayed = 0;

        // Start the game loop for multiple rounds
        while (true) {
            roundsPlayed++;
            System.out.println("\nRound " + roundsPlayed);

            // Generate a random number between 1 and 100
            int numberToGuess = random.nextInt(100) + 1;
            int attemptsLeft = 10;
            boolean guessedCorrectly = false;

            // Start the guessing loop
            while (attemptsLeft > 0 && !guessedCorrectly) {
                System.out.println("You have " + attemptsLeft + " attempts remaining.");
                System.out.print("Enter your guess (between 1 and 100): ");
                int userGuess = scanner.nextInt();

                // Compare the guess with the generated number
                if (userGuess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else if (userGuess > numberToGuess) {
                    System.out.println("Too high! Try again.");
                } else {
                    System.out.println("Correct! The number was " + numberToGuess + ".");
                    guessedCorrectly = true;
                }

                attemptsLeft--;
            }

            // If the user doesn't guess correctly in time, reveal the number
            if (!guessedCorrectly) {
                System.out.println("Sorry, you ran out of attempts. The number was " + numberToGuess + ".");
            }

            // Calculate score based on remaining attempts
            int score = guessedCorrectly ? attemptsLeft : 0;
            totalScore += score;
            System.out.println("You earned " + score + " points this round.");

            // Ask if the user wants to play another round
            System.out.print("Do you want to play again? (y/n): ");
            String playAgain = scanner.next();
            if (!playAgain.equalsIgnoreCase("y")) {
                break;
            }
        }

        // Display total score and rounds played
        System.out.println("\nGame Over! You played " + roundsPlayed + " rounds.");
        System.out.println("Your total score is " + totalScore + " points.");
        scanner.close();
    }
}




    

