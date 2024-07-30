import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a binary number: ");
        String binaryInput = scanner.nextLine();

        // Checking if the input is a valid binary number
        if (isValidBinary(binaryInput)) {
            int decimalResult = binaryToDecimal(binaryInput);
            System.out.println("Decimal equivalent: " + decimalResult);
        } else {
            System.out.println("Invalid binary number. Please enter a valid binary number.");
        }

        scanner.close();
    }

    private static boolean isValidBinary(String binary) {
        // Check if the input contains only 0s and 1s
        return binary.matches("[01]+");
    }

    private static int binaryToDecimal(String binary) {
        int decimalResult = 0;
        int binaryLength = binary.length();

        // Iterate through each digit of the binary number
        for (int i = 0; i < binaryLength; i++) {
            int digit = Character.getNumericValue(binary.charAt(i));

            // Calculate the decimal equivalent using the positional value
            decimalResult += digit * Math.pow(2, binaryLength - i - 1);
        }

        return decimalResult;
    }
}
