import java.time.DayOfWeek;
import java.time.LocalDate;
import java.util.Scanner;

public class CalendarPrinter {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        // --- Input ---
        System.out.print("Enter year: ");
        int year = input.nextInt();
        System.out.print("Enter month (1-12): ");
        int month = input.nextInt();

        // --- Title ---
        System.out.println("\nCalendar for the month of " + 
            LocalDate.of(year, month, 1).getMonth() + ", " + year);
        System.out.println("Su  Mo  Tu  We  Th  Fr  Sa");

        // --- Find first day of the month ---
        LocalDate date = LocalDate.of(year, month, 1);
        DayOfWeek firstDay = date.getDayOfWeek();
        int dayValue = firstDay.getValue(); // Monday = 1, Sunday = 7

        // --- Adjust to make Sunday = 0 ---
        int startIndex = dayValue % 7;

        // --- Print leading spaces ---
        for (int i = 0; i < startIndex; i++) {
            System.out.print("    ");
        }

        // --- Print days ---
        int lengthOfMonth = date.lengthOfMonth();
        for (int day = 1; day <= lengthOfMonth; day++) {
            System.out.printf("%2d  ", day);
            if ((day + startIndex) % 7 == 0) {
                System.out.println();
            }
        }

        input.close();
    }
}
