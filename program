import java.io.*;
import java.util.Scanner;

public class FileOperations {

    public static void main(String[] args) {
        String filePath = "example.txt";

        // Write to file
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filePath))) {
            writer.write("This is the first line.\n");
            writer.write("This is the second line.\n");
        } catch (IOException e) {
            System.err.println("Error writing to file: " + e.getMessage());
        }

        // Read from file
        try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {
            String line;
            System.out.println("Reading from file:");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.err.println("Error reading from file: " + e.getMessage());
        }

        // Modify file (append)
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filePath, true))) {
            writer.write("This line is appended.\n");
        } catch (IOException e) {
            System.err.println("Error appending to file: " + e.getMessage());
        }

        // Read and modify file (replace a line)
         File inputFile = new File(filePath);
        File tempFile = new File("temp.txt");

        try (BufferedReader reader = new BufferedReader(new FileReader(inputFile));
             BufferedWriter writer = new BufferedWriter(new FileWriter(tempFile))) {

            String line;
            while ((line = reader.readLine()) != null) {
                if (line.equals("This is the second line.")) {
                    writer.write("This line replaced the second line.\n");
                } else {
                    writer.write(line + "\n");
                }
            }
        } catch (IOException e) {
            System.err.println("Error processing file: " + e.getMessage());
            return;
        }

        //Replace original file with temp file
        if (!inputFile.delete()) {
            System.err.println("Could not delete original file");
            return;
        }
        if (!tempFile.renameTo(inputFile)) {
            System.err.println("Could not rename temp file");
        }

        // Read modified file
        try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {
            String line;
            System.out.println("Reading modified file:");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.err.println("Error reading modified file: " + e.getMessage());
        }
    }
}
