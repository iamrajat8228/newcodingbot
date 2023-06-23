import java.util.ArrayList;
import java.util.Scanner;

public class Train {

    private String trainName;
    private int totalSeats;
    private int seatsBooked;

    public Train(String trainName, int totalSeats, int seatsBooked) {
        this.trainName = trainName;
        this.totalSeats = totalSeats;
        this.seatsBooked = seatsBooked;
    }

    public String getTrainName() {
        return trainName;
    }

    public int getTotalSeats() {
        return totalSeats;
    }

    public int getSeatsBooked() {
        return seatsBooked;
    }

    public int getAvailableSeats() {
        return totalSeats - seatsBooked;
    }

    public void reserveSeats(int numSeats) {
        if (numSeats > getAvailableSeats()) {
            System.out.println("Sorry, there are not enough seats available on this train.");
            return;
        }

        seatsBooked += numSeats;
        System.out.println("Seats reserved successfully!");
    }
}

class TrainReservationSystem {
    private ArrayList<Train> trains;

    public TrainReservationSystem() {
        trains = new ArrayList<>();
    }

    public void addTrain(Train train) {
        trains.add(train);
    }

    public void displayAvailableTrains() {
        System.out.println("Available Trains:");
        for (Train train : trains) {
            System.out.println(train.getTrainName() + " - Available Seats: " + train.getAvailableSeats());
        }
    }

    public Train getTrainByName(String trainName) {
        for (Train train : trains) {
            if (train.getTrainName().equalsIgnoreCase(trainName)) {
                return train;
            }
        }
        return null;
    }
    public class TrainReservationApp {
        public static void main(String[] args) {
            TrainReservationSystem reservationSystem = new TrainReservationSystem();

            // Adding sample trains
            Train train1 = new Train("Express 1", 100, 10);
            Train train2 = new Train("Express 2", 150, 50);
            Train train3 = new Train("Superfast 1", 200, 100);

            reservationSystem.addTrain(train1);
            reservationSystem.addTrain(train2);
            reservationSystem.addTrain(train3);

            Scanner scanner = new Scanner(System.in);

            System.out.println("Welcome to the Online Train Reservation System!");

            while (true) {
                System.out.println("\nMENU:");
                System.out.println("1. View Available Trains");
                System.out.println("2. Reserve Seats");
                System.out.println("3. Exit");

                System.out.print("Enter your choice (1-3): ");
                int choice = scanner.nextInt();
                scanner.nextLine(); // Consume newline character

                if (choice == 1) {
                    reservationSystem.displayAvailableTrains();
                } else if (choice == 2) {
                    System.out.print("Enter the name of the train: ");
                    String trainName = scanner.nextLine();

                    Train train = reservationSystem.getTrainByName(trainName);
                    if (train == null) {
                        System.out.println("Train not found!");
                        continue;
                    }

                    System.out.print("Enter the number of seats to reserve: ");
                    int numSeats = scanner.nextInt();
                    scanner.nextLine(); // Consume newline character

                    train.reserveSeats(numSeats);
                } else if (choice == 3) {
                    System.out.println("Thank you for using the Online Train Reservation System. Goodbye!");
                    break;
                } else {
                    System.out.println("Invalid choice");




}


	}

 }}}

