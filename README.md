# digibhem.1
import java.util.Scanner;

class BookMyShow {
    private String movieName;
    private String movieLanguage;
    private int movieRating;
    private int showTimings[];
    private String[] seatsBooked;

    public BookMyShow(String movieName, String movieLanguage, int movieRating, int showTimings[], String[] seatsBooked) {
        this.movieName = movieName;
        this.movieLanguage = movieLanguage;
        this.movieRating = movieRating;
        this.showTimings = showTimings;
        this.seatsBooked = seatsBooked;
    }

    public String getMovieName() {
        return movieName;
    }

    public String getMovieLanguage() {
        return movieLanguage;
    }

    public int getMovieRating() {
        return movieRating;
    }

    public int[] getShowTimings() {
        return showTimings;
    }

    public String[] getSeatsBooked() {
        return seatsBooked;
    }

    public void bookSeat(int timingIndex, String seatNumber) {
        if (seatsBooked[timingIndex] == null) {
            seatsBooked[timingIndex] = seatNumber;
        } else {
            System.out.println("Seat already booked.");
        }
    }

    public void cancelSeat(int timingIndex) {
        if (seatsBooked[timingIndex] != null) {
            seatsBooked[timingIndex] = null;
        } else {
            System.out.println("No seat to cancel.");
        }
    }

    public void displaySeats() {
        for (int i = 0; i < showTimings.length; i++) {
            System.out.println("Showtime: " + showTimings[i] + " - Seat Number: " + (seatsBooked[i] == null ? "Not Booked" : seatsBooked[i]));
        }
    }
}

    public class main { 
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        BookMyShow movie1 = new BookMyShow("Movie1", "Hindi", 4, new int[]{1200, 1500, 1800, 2100}, new String[4]);
        BookMyShow movie2 = new BookMyShow("Movie2", "English", 3, new int[]{1300, 1600, 1900, 2200}, new String[4]);

        while (true) {
            System.out.println("Enter 1 to book a ticket for Movie1");
            System.out.println("Enter 2 to book a ticket for Movie2");
            System.out.println("Enter 3 to display all booked seats");
            System.out.println("Enter 4 to cancel a booked seat");
            System.out.println("Enter 0 to exit");

            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Enter showtime index: ");
                    int showIndex1 = sc.nextInt();
                    System.out.println("Enter seat number: ");
                    String seatNumber1 = sc.next();
                    movie1.bookSeat(showIndex1, seatNumber1);
                    break;
                case 2:
                    System.out.println("Enter showtime index: ");
                    int showIndex2 = sc.nextInt();
                    System.out.println("Enter seat number: ");
                    String seatNumber2 = sc.next();
                    movie2.bookSeat(showIndex2, seatNumber2);
                    break;
                case 3:
                    System.out.println("Booked Seats: ");
                    System.out.println("Movie1: ");
                    movie1.displaySeats();
                    System.out.println("Movie2: ");
                    movie2.displaySeats();
                    break;
                case 4:
                    System.out.println("Enter 1 to cancel a booked seat for Movie1");
                    System.out.println("Enter 2 to cancel a booked seat for Movie2");
                    int cancelChoice = sc.nextInt();
                    if (cancelChoice == 1) {
                        System.out.println("Enter showtime index: ");
                        int cancelIndex1 = sc.nextInt();
                        movie1.cancelSeat(cancelIndex1);
                    } else if (cancelChoice == 2) {
                        System.out.println("Enter showtime index: ");
                        int cancelIndex2 = sc.nextInt();
                        movie2.cancelSeat(cancelIndex2);
                    } else {
                        System.out.println("Invalid choice");
                    }
                    break;
                case 0:
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice");
                    break;
            }
        }
    }
}
