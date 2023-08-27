# Java- Guessing a number
import java.util.Scanner;
import java.util.Random;

public class EnhancedNumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int lowerBound = 1;
        int upperBound = 100;
        int numberOfAttempts = 0;

        System.out.println("Welcome to the Enhanced Number Guessing Game!");
        System.out.println("Choose a difficulty level:");
        System.out.println("1. Easy (1-100, unlimited attempts)");
        System.out.println("2. Medium (1-100, 10 attempts)");
        System.out.println("3. Hard (1-100, 5 attempts)");
        System.out.print("Enter the level number: ");
        
        int levelChoice = scanner.nextInt();
        int maxAttempts = 0;

        switch (levelChoice) {
            case 1:
                maxAttempts = Integer.MAX_VALUE;
                break;
            case 2:
                maxAttempts = 10;
                break;
            case 3:
                maxAttempts = 5;
                break;
            default:
                System.out.println("Invalid choice. Defaulting to Medium level.");
                maxAttempts = 10;
                break;
        }

        int randomNumber = random.nextInt(upperBound - lowerBound + 1) + lowerBound;
        boolean hasWon = false;

        System.out.println("I have selected a number between " + lowerBound + " and " + upperBound + ".");
        System.out.println("You have " + maxAttempts + " attempts to guess it.");

        while (numberOfAttempts < maxAttempts) {
            System.out.print("Attempt " + (numberOfAttempts + 1) + "/" + maxAttempts + ": Enter your guess: ");
            int playerGuess = scanner.nextInt();
            numberOfAttempts++;

            if (playerGuess < randomNumber) {
                System.out.println("Too low! Try again.");
            } else if (playerGuess > randomNumber) {
                System.out.println("Too high! Try again.");
            } else {
                hasWon = true;
                break;
            }
        }

        if (hasWon) {
            System.out.println("Congratulations! You guessed the number " + randomNumber + " in " + numberOfAttempts + " attempts.");
        } else {
            System.out.println("Sorry, you've reached the maximum number of attempts. The correct number was: " + randomNumber);
        }

        scanner.close();
    }
}
