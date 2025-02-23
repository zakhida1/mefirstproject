import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.security.SecureRandom;
import java.util.Scanner;

public class PasswordGenerator {
    private static final String LOWER_CASE = "abcdefghijklmnopqrstuvwxyz";
    private static final String UPPER_CASE = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    private static final String NUMBERS = "0123456789";
    private static final String SYMBOLS = "!@#$%^&*()-_+=[]{}|;':\",./<>?";

    public static String generatePassword(int minLength, int maxLength, String types) {
        if (minLength > maxLength || minLength <= 0) {
            throw new IllegalArgumentException("Invalid password length.");
        }

        StringBuilder availableChars = new StringBuilder();
        if (types.contains("1")) availableChars.append(LOWER_CASE);
        if (types.contains("2")) availableChars.append(UPPER_CASE);
        if (types.contains("3")) availableChars.append(NUMBERS);
        if (types.contains("4")) availableChars.append(SYMBOLS);

        if (availableChars.isEmpty()) {
            throw new IllegalArgumentException("At least one character type must be selected.");
        }

        SecureRandom random = new SecureRandom();
        int passwordLength = random.nextInt(maxLength - minLength + 1) + minLength;
        StringBuilder password = new StringBuilder(passwordLength);

        for (int i = 0; i < passwordLength; i++) {
            int randomIndex = random.nextInt(availableChars.length());
            password.append(availableChars.charAt(randomIndex));
        }

        return password.toString();
    }

    public static void main(String[] args) throws IOException {
        Scanner fileScanner = new Scanner(new File("test_files/input.txt"));
        int minLength = fileScanner.nextInt();
        int maxLength = fileScanner.nextInt();
        String types = fileScanner.next();
        fileScanner.close();

        String password = generatePassword(minLength, maxLength, types);
        System.out.println("Generated password: " + password);

        FileWriter writer = new FileWriter("test_files/output.txt");
        writer.write("Minimum password length: " + minLength + "\n");
        writer.write("Maximum password length: " + maxLength + "\n");
        writer.write("Types: " + types + "\n");
        writer.write("Generated password: " + password + "\n");
        writer.close();

        System.out.println("Password written to test_files/output.txt");
    }
}
