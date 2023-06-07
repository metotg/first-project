import java.util.Scanner;
import java.io.FileWriter;
import java.io.IOException;

public class Main {
    public static String isStringsAreMirroring(String input) {
        if (input.charAt(0) != input.charAt(input.length() - 1)) {
            return "No mirrored part";
        }

        String repeatingSection = "";
        for (int i = 1; i < input.length() - 1; i++) {
            if (Character.toLowerCase(input.charAt(i)) == Character.toLowerCase(input.charAt(input.length() - 1 - i))) {
                repeatingSection += Character.toLowerCase(input.charAt(i));
            } else {
                break;
            }
        }

        if (repeatingSection.isEmpty()) {
            return "No mirrored part";
        } else {
            return repeatingSection;
        }
    }

    public static int countWordsEndingInYZ(String input) {
        String[] words = input.split("\\s+");
        int count = 0;
        for (String word : words) {
            char lastChar = Character.toLowerCase(word.charAt(word.length() - 1));
            if (lastChar == 'y' || lastChar == 'z') {
                count++;
            }
        }
        return count;
    }
    public static void printTriangle(int n) {
        try {
            FileWriter fileWriter = new FileWriter("triangle.txt");
            for (int i = 1; i <= n; i++) {
                for (int j = 1; j <= i; j++) {
                    fileWriter.write("!");
                    System.out.print("!");
                }
                fileWriter.write("\n");
                System.out.println();
            }
            fileWriter.close();
        } catch (IOException e) {
            System.out.println("An error occurred while writing to the file.");
            e.printStackTrace();
        }
    }
    public static void drawSquareFrame(int n) {
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n; j++) {
                if (i == 1 || i == n || j == 1 || j == n) {
                    System.out.print("? ");
                } else {
                    System.out.print("- ");
                }
            }
            System.out.println();
        }
    }


    public static void main(String[] args) {
        System.out.println("Enter the string to check if it is mirroring:");
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine();

        String repeatingSection = isStringsAreMirroring(input);
        System.out.println("Mirroring Section: " + repeatingSection);

        int wordCountYZ = countWordsEndingInYZ(input);
        System.out.println("Count of words ending in 'y' or 'z': " + wordCountYZ);
        System.out.println("Enter the value of n for the triangle:");
        int n = sc.nextInt();

        printTriangle(n);
        System.out.println("Triangle printed and saved to triangle.txt");
        System.out.print("Въведете цяло положително число n: ");
        int N = sc.nextInt();

        drawSquareFrame(N);
    }

    }

