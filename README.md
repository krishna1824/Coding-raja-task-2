Step 1-Importing the necessary modules and libraries:
In this step, we will import all the libraries and modules that we will use to create this project.

Step 2-Connecting to the database and creating the GUI window:
Explanation:

1. In this step, we will connect our Python script to the SQLite database. Here all the information will be stored and our GUI window.

2. To connect to the database,

We will create a connector instance using the sqlite.connector (<database name>) to create a database, activate it and perform functions in the database using the script.
3. To create our GUI window, we will first create a Tk object that will become our main window. Then we will set its basic attributes and move onto placing components and widgets in it.

4. Our first widget is the static text saying “Expense Tracker” (a Label widget) packed at the top of the window.

5. Next, we have three Frame widgets (widgets containers inside a window) that will contain different aspects of our GUI window.

6. The frame on the left side of the window contains Labels and Entry fields. Here the details about a new expense can be entered, or the details about an existing expense can be viewed. This frame also has two buttons, one that adds the expense to the database when pressed. The other can show how you read the expense, before you add it to the database.


7. The frame on the bottom-right side of the window contains a Treeview object. This acts as a table where the data from the database tables is displayed.

8. The frame on the top-right side of the window contains the buttons that can perform certain operations on the expense selected in the table, or the database as a whole such as editing the selected expense, converting it to words, delete it or delete the entire database.

Step 3-Creating the database and data manipulation functions
Explanation:

In this step, we will create all the functions for all the buttons on our Expense Tracker window.


The one common thing in all the functions is that we will make the scope of all the Entry fields and the database connector in the left frame global by using the global keyword.


One common thing in all the functions that perform an operation regarding one single expense is that if there is no selection in the table, it will display an error message using the mb.showerror() function.

Another common thing in all the functions that deal with data are two statements, connector.execute() and connector.commit(). The first statement takes an argument, which is supposed to be an SQL command, is used to execute that argument as in an SQL engine and the second one is used to finalize that change and perform it in the database.

In the list_all_expenses() function, we will delete all the children of the table, then get all the data from the database table using the connector’s SELECT command and then we will insert all of it to the table using the .insert() method of it.

In the view_expense_details(), we will get the values in the currently selected item of the table. Then set the values of the StringVar, IntVar or DateEntry variables to the corresponding indices of the tuple containing the values of the said selected item.

In the clear_fields() function, we will set all the StringVar variables to an empty string and the DataEntry variable to the current date.

In the remove_expense() function, we will get the values of the currently selected item in the table, and ask the user if he really wants to delete it. If he/she wants to delete it, we will delete it using the DELETE command in the execute-commit method combo of the connector.

In the remove_all_expenses() function, we will first ask the user if they are sure that they want to delete all the expenses that we have stored for them using the messagebox.askyesno() function. If they reply yes, we will delete using the DELETE * FROM <tablename> command as an argument to the connector.execute() and the connector.commit() methods.

In the add_another_expense() function, if any of the Entry fields is empty, we will display an error message box, otherwise we will enter the INSERT command in the connector’s execute-commit methods combination, then clear all the entry fields and display the updated table.

The edit_expense() function only makes changes in the components present on the window. However, with the nested edit_existing_expense() function, we get the contents of the selected record in the table and then use the UPDATE command to edit the data in the table with the help of the ID of the expense, which the user cannot edit.

In the selected_words_to_expense() function, we will simply check if there is a selection in the table. If there is, we will display an information box with the message telling the user how to read the expense using the mb.showinfo() function.

The expense_to_words_before_adding() function is to tell the user how to read their expense before they add it to the database. This is to make sure that they are confident with the data entered, and how it will be interpreted by others. In that function, we will take the contents of the Entry fields and do something similar to the previous function, except the information box will now be a ask-yes-or-no box where, if the user presses yes, the expense will be added to the database


