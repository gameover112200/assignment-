
import java.util.Scanner;

public class SmartRestaurantOrder {
    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        double drinkPrice = 15.50;
        double studentDiscount = 0.10;
        double seniorDiscount = 0.05;
        double tipRate = 0.10;

        System.out.print("Enter customer name: ");
        String name = input.nextLine();

        System.out.print("Enter age: ");
        int age = input.nextInt();

        System.out.print("Enter meal price: ");
        double mealPrice = input.nextDouble();

        System.out.print("Enter number of drinks: ");
        int drinks = input.nextInt();

        System.out.print("Is the customer a student? (true/false): ");
        boolean student = input.nextBoolean();

        System.out.print("Enter service rating (1-5): ");
        int rating = input.nextInt();

        if (rating >= 1 && rating <= 5) {

            double drinksCost = drinks * drinkPrice;
            double total = mealPrice + drinksCost;

            double discount = 0;

            if (student == true) {
                discount = total * studentDiscount;
            }
            else if (age >= 60) {
                discount = total * seniorDiscount;
            }
            else {
                discount = 0;
            }

            double newTotal = total - discount;

            double tip = 0;

            if (rating >= 4) {
                tip = newTotal * tipRate;
            }
            else {
                tip = 0;
            }

            double finalBill = newTotal + tip;

            int wholeAmount = (int) finalBill;

            System.out.println();
            System.out.println("SMART RESTAURANT");
            System.out.println("Customer: " + name);
            System.out.println("Meal: " + mealPrice);
            System.out.println("Drinks: " + drinksCost);
            System.out.println("Discount: " + discount);
            System.out.println("Tip: " + tip);
            System.out.println("Final bill: " + finalBill);
            System.out.println("Whole amount: " + wholeAmount);

        }
        else {
            System.out.println("Error: rating must be between 1 and 5");
        }

        input.close();
    }
}

