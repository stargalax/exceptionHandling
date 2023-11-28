If you cant access the code form the repo copy paste the below code in your complier! 

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter integers separated by spaces:");
        String input = scanner.nextLine();
        String[] numbers = input.split(" ");

        try {
            printRepeatedIntegers(numbers);
        } catch (DuplicateFoundException e) {
            System.out.println(e.getMessage());
        }
    }

    static void printRepeatedIntegers(String[] numbers) throws DuplicateFoundException {
        boolean foundRepeated = false;

        for (int i = 0; i < numbers.length - 1; i++) {
            int count = 1;
            if (numbers[i] == null) {
                continue;
            }
            for (int j = i + 1; j < numbers.length; j++) {
                if (numbers[i].equals(numbers[j])) {
                    count++;
                    numbers[j] = null; // Mark as counted
                }
            }
            if (count > 1) {
                foundRepeated = true;
                System.out.println("Number: " + numbers[i] + " is repeated " + count + " times.");
            }
        }

        if (!foundRepeated) {
            throw new DuplicateFoundException("No duplicates found.");
        }
    }
}

class DuplicateFoundException extends Exception {
    public DuplicateFoundException(String message) {
        super(message);
    }
}
