package sample;

import javafx.fxml.FXML;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;


public class Controller {
    //Writing all my labels, global variables, and text field.
    @FXML
    TextField txtInput;
    @FXML
    Label burgerDisplay, saladDisplay, sandwichDisplay, tacosDisplay, friesDisplay, sodaDisplay, subTotalDisplay, totalDisplay, change1, change2, change3, change4, change5, change6, change7, change8, change9, change10, notEnough, changeDisplay;
    double burgerPrice, saladPrice, sandwichPrice, tacosPrice, friesPrice, sodaPrice, subTotal, total, change;
    int dollarChange, cents;

    //Function that starts the program when the start button is clicked, running 2 functions for the program to work.
    @FXML
    private void startProgram() {
        resetStuff();
        generatePrices();

    }

    //This resets the total prices and the total and subtotal displays in case someone wants to restart the program without stopping and rerunning it.
    public void resetStuff() {
        //Sets my subtotal and total to 0 when restarting the program.
        subTotal = 0.00;
        total = 0.00;
        //Sets the subtotal and total text to 0 once the program is restarted.
        subTotalDisplay.setText("$" + subTotal);
        totalDisplay.setText("$" + total);

    }

    //Function that generates random prices each time the button is clicked; It also sets the label for that specific food to the new random price generated every time.
    public void generatePrices() {
        //These all pass an upper and lower bound to a random number function, which generates the random prices for the foods.
        burgerPrice = randomNum(800, 400);
        saladPrice = randomNum(800, 400);
        sandwichPrice = randomNum(400, 200);
        tacosPrice = randomNum(300, 100);
        friesPrice = randomNum(200, 100);
        sodaPrice = randomNum(150, 100);
        //These all pass the food prices to a set prices function, which sets the labels corresponding to each food with their correct prices.
        burgerDisplay.setText(setPricesText(burgerPrice));
        saladDisplay.setText(setPricesText(saladPrice));
        sandwichDisplay.setText(setPricesText(sandwichPrice));
        tacosDisplay.setText(setPricesText(tacosPrice));
        friesDisplay.setText(setPricesText(friesPrice));
        sodaDisplay.setText(setPricesText(friesPrice));
    }

    //This is the random number function that generates the random price for the foods given the lower and upper bounds (range of prices).
    public double randomNum(double upper, double lower) {
        //This is the random number code which returns a random number within those given lower and upper bounds.
        return ((Math.floor(Math.random() * (upper - lower + 1)) + lower) / 100);
    }

    //This is the function that returns the price with a $ sign so that it can be displayed, and also checks for a digit that is missing that will be explained below.
    public String setPricesText(double price) {
        //Since all the prices are greater than $1 and less than $10, this checks if the price is 3 characters. The price should always be 4 characters (ex. 1.21, 5.23, etc.). If the price is 3 characters, the amount ends in a 0 (ex. 1.20, 5.70) and it is actually displaying 1.2 or 5.7. This code segment adds a "0" to that number to make it look normal and realistic, changing them to 1.20 and 5.70.
        if (Double.toString(price).length() == 3) {
            //Returns the price with the dollar sign and extra 0 added.
            return ("$" + price + "0");
        } else {
            //Returns the price with the dollar sign added.
            return ("$" + price);
        }
    }

    //When the button to add a burger to your subtotal is clicked, this function runs, adding the burger price to the subtotal and updating the subtotal with the new price.
    @FXML
    private void burgerAdd() {
        //Adds the burger price to the subtotal amount.
        subTotal += burgerPrice;
        //Sets the subtotal display to the result of a string add function; It passes the subtotal amount as a parameter, and then the function checks for a common error and returns the subtotal with a $ sign added to it.
        subTotalDisplay.setText(stringAdd(subTotal));
    }

    //When the button to add a salad to your subtotal is clicked, this function runs, adding the salad price to the subtotal and updating the subtotal with the new price.
    @FXML
    private void saladAdd() {
        //Adds the salad price to the subtotal amount.
        subTotal += saladPrice;
        //Sets the subtotal display to the result of a string add function; It passes the subtotal amount as a parameter, and then the function checks for a common error and returns the subtotal with a $ sign added to it.
        subTotalDisplay.setText(stringAdd(subTotal));
    }

    //When the button to add a sandwich to your subtotal is clicked, this function runs, adding the sandwich price to the subtotal and updating the subtotal with the new price.
    @FXML
    private void sandwichAdd() {
        //Adds the sandwich price to the subtotal amount.
        subTotal += sandwichPrice;
        //Sets the subtotal display to the result of a string add function; It passes the subtotal amount as a parameter, and then the function checks for a common error and returns the subtotal with a $ sign added to it.
        subTotalDisplay.setText(stringAdd(subTotal));
    }

    //When the button to add tacos to your subtotal is clicked, this function runs, adding the tacos price to the subtotal and updating the subtotal with the new price.
    @FXML
    private void tacosAdd() {
        //Adds the tacos price to the subtotal amount.
        subTotal += tacosPrice;
        //Sets the subtotal display to the result of a string add function; It passes the subtotal amount as a parameter, and then the function checks for a common error and returns the subtotal with a $ sign added to it.
        subTotalDisplay.setText(stringAdd(subTotal));
    }

    //When the button to add fries to your subtotal is clicked, this function runs, adding the fries price to the subtotal and updating the subtotal with the new price.
    @FXML
    private void friesAdd() {
        //Adds the fries price to the subtotal amount.
        subTotal += friesPrice;
        //Sets the subtotal display to the result of a string add function; It passes the subtotal amount as a parameter, and then the function checks for a common error and returns the subtotal with a $ sign added to it.
        subTotalDisplay.setText(stringAdd(subTotal));
    }

    //When the button to add a soda to your subtotal is clicked, this function runs, adding the soda price to the subtotal and updating the subtotal with the new price.
    @FXML
    private void sodaAdd() {
        //Adds the soda price to the subtotal amount.
        subTotal += sodaPrice;
        //Sets the subtotal display to the result of a string add function; It passes the subtotal amount as a parameter, and then the function checks for a common error and returns the subtotal with a $ sign added to it.
        subTotalDisplay.setText(stringAdd(subTotal));
    }

    //Function that adds a $ sign to the price, and checks for a common error, and returns the full string.
    public String stringAdd(double num) {
        //This checks for the error caused sometimes in doubles where a repeated decimal is displayed; With this method, it rounds the price to the nearest hundredth to prevent this error from occurring.
        if (Double.toString(num).length() > 8) {
            //This returns the rounded number with the dollar sign.
            return ("$" + (Math.floor(100 * (num))) / 100);
        } else {
            //If the price does not need to be rounded, it will just return it with the dollar sign.
            return ("$" + num);
        }
    }

    //Function that adds tax and displays the full total amount once the add tax button is clicked.
    @FXML
    private void addTax() {
        //Displays the total price including tax, with a $ sign.
        totalDisplay.setText("$" + (Math.floor(110 * (subTotal))) / 100);
        //Sets total variable to equal full total price, including tax.
        total = (Math.floor(110 * (subTotal)) / 100);
    }

    //This function calculates the change needed to be given to the customer.
    @FXML
    private void calcChange() {
        //Sets the change variable to the difference of how much the customer pays with and how much the total price is.
        change = (Double.parseDouble(txtInput.getText())) - total;

        //Checks if this boolean function is true to determine whether to run this code or not, based on if the customer needs change or not.
        if (checkChange()) {

            //This checks for the error caused sometimes in doubles where a repeated decimal is displayed; With this method, it rounds the change to the nearest hundredth to prevent this error from occurring.
            if (Double.toString(change).length() > 8) {
                change = Math.round(100 * change);
                change /= 100;
            }

            //Sets the variable for the amount of change in dollars (not including cents) equal to the current change variable, as an integer.
            dollarChange = (int) (change);

            //Sets the variable for the amount of change in cents equal to the remainder of the change in dollars; This is a double variable since the change is displayed in decimals.
            double centsChange = ((((((change % 100) % 50) % 20) % 10) % 5) % 1);

            //This checks for the error caused sometimes in doubles where a repeated decimal is displayed; With this method, it rounds the cents change to the nearest hundredth to prevent this error from occurring.
            if (Double.toString(centsChange).length() > 8) {
                centsChange = Math.round(centsChange * 100);
                centsChange /= 100;

            }

            //This multiples the cents change by 100 so that it can be used as an integer, making it a lot easier.
            centsChange *= 100;
            //Sets cents variable as an integer of the cents change variable
            cents = (int) (centsChange);

            //These 10 lines of code sets each of the 10 text labels at the end to display the amount of that denomination of money that they will get back in change; It passes through a check change function, and here I pass through the denomination type and the amount of total change corresponding to whether it is in dollars or cents.
            change1.setText(getDollarChange(100, dollarChange) + " $100 bills");
            change2.setText(getDollarChange(50, dollarChange) + " $50 bills");
            change3.setText(getDollarChange(20, dollarChange) + " $20 bills");
            change4.setText(getDollarChange(10, dollarChange) + " $10 bills");
            change5.setText(getDollarChange(5, dollarChange) + " $5 bills");
            change6.setText(getDollarChange(1, dollarChange) + " $1 bills");
            change7.setText(getCentsChange(25, cents) + " quarters");
            change8.setText(getCentsChange(10, cents) + " dimes");
            change9.setText(getCentsChange(5, cents) + " nickels");
            change10.setText(getCentsChange(1, cents) + " pennies");
        }
    }

    //This boolean function checks to see if the user needs change or not; if they do, it will return true, and if not, it will return false.
    public boolean checkChange() {
        //if the user underpays, it will display that the user did not pay enough money and return false so the change function doesn't run.
        if (change < 0) {
            notEnough.setText("You haven't payed enough.");
            return false;
            //if the user pays the exact amount, it will display that the user has no change and return false so the change function doesn't run.
        } else if (change == 0) {
            notEnough.setText("You have no change.");
            return false;
        } else {
            //if the user pays more than the total, it will display that the user has change and return true so the change function does run.
            notEnough.setText("You have change.");
            changeDisplay.setText(stringAdd(change));
            return true;
        }
    }

    //This function checks how much change the user gets back in dollars, and returns the amount.
    public int getDollarChange(int changeAmt, int change) {
        //This subtracts the amount of change being returned from the total change in dollars variable, so it is updated in case run again.
        dollarChange %= changeAmt;
        //This divides the change by the denomination, returning how many of that denomination of money should be given back in change.
        return change / changeAmt;
    }

    //This function checks how much change the user gets back in cents, and returns the amount.
    public int getCentsChange(int changeAmt, int change) {
        //This subtracts the amount of change being returned from the total change in cents variable, so it is updated in case run again.
        cents %= changeAmt;
        //This divides the change by the denomination, returning how many of that denomination of money should be given back in change.
        return change / changeAmt;

    }

}