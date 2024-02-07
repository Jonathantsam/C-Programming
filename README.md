# C-Programming


4
MMA Weight Classes
A program to allow the user to determine the weight classification of a fighter. The user
will enter the weight of the fighter in pounds and the program will print out the
classification:
1. Super Heavyweight: Unlimited
2. Heavyweight: Limit - 265 pounds
3. Cruiserweight: Limit - 225 pounds
4. Light Heavyweight: Limit - 205 pounds
5. Super Middleweight: Limit - 195 pounds
6. Middleweight: Limit - 185 pounds
7. Super Welterweight: Limit - 175 pounds
8. Welterweight: Limit - 170 pounds
9. Super Lightweight: Limit - 165 pounds
10. Lightweight: Limit - 155 pounds
11. Featherweight: Limit - 145 pounds
12. Bantamweight: Limit - 135 pounds
13. Flyweight: Limit - 125 pounds
14. Strawweight: Limit - 115 pounds
Your program should assume that a fighter will always fight in the lightest classification
their weight allows, i.e. someone who weighs 104 pounds could enter a Heavyweight
contest, but I don't think they would enjoy it...
3) Repeating Behaviours
We can now make simple programs that read in some data (film number and age), do
something with it (decide if you can see the film or not) and display a result (print the
message).
We have noticed that sometimes our program wants to repeat a behaviour, either
because it didn’t work first time (the user entered a film number that is not valid) or
because we want to do something more than once (perhaps we want to deal with another
customer). To do this we need a program construction that lets us repeat a set of C#
program statements multiple times (perhaps we want to handle 100 customers), or
continue performing a statement until some condition is met (perhaps we want to keep
looping while the user gives is stupid values).
Validating inputs
Programmers call it “validation”. We call it “making sure you don’t get stupid values from
your user”. In the case of the cinema entry program you will somewhere have to deal with
the user putting in stupid numbers in two different situations, giving the film number and
giving their age. In both these situations we want the program to keep on asking for a
numeric value while the user gives them invalid ones.
Validating the Film Number
In the case of the film number we will have something like this, where what the user types
is underlined:
5
Welcome to Famous Players
We are presently showing:
1. Species (14)
2. Fight Club (14)
3. Stargate (PG) // any age
4. The Terminator (18)
5. Surf’s Up (F) // any age
Enter the number of the film you wish to see: 1
If the user makes a mistake you might find something like this:
Enter the number of the film you wish to see: 9
There is no film with the number 9, and so we want to reject this. In fact, if the user gives
a film number which is less than 1 or greater than 5 we want to reject this. It turns out that
we can combine these two tests into a single condition, using a logical or.
if ((filmNumber < 1) || (filmNumber > 5))
{
// if we get here the age is wrong
} else {
// if we get here the age is OK
}
You can find out more about the if condition and the tests you can
do in the C# Yellow Book on page 39.
Remember that if you use this code you need to use the variable you created to hold the
film number (I called it filmNumber) in your code.
Making Loops to Validate the film number
You can use the above code to make an easy test for the age, but what you really want to
do is loop around if the age is wrong. You want to do the read operation while the number
given is wrong. To do this we can use the rather aptly named do-while loop.
do {
// read in the value of filmNumber
} while ((filmNumber < 1) || (filmNumber > 5));
// When we get here we must have a valid film number
This loop will go round until the user types in a valid film number value. In other words, as
long as the condition is true, this loop will repeat.
6
You can find out more about loops in the C# Yellow Book on
page 43.
Now that we know about loops we can modify our program to repeatedly request film
number values until the user enters a valid one.
Before you go any further; perform the following:
1. Make a copy of you project for Part 1.
2. Modify the Program.cs program so that it refuses to accept a
film number which is outside the range 1 to 5.
3. Use the same technique to ensure that ages are entered in the
range 5 to 120. These are the minimum and maximum age
values that the cinema manager wants you to use.
Making your program user friendly
Ideally your program should give messages to tell the user that they have done
something wrong:
Welcome to Famous Players
We are presently showing:
1. Species (14)
2. Fight Club (14)
3. Stargate (PG) // any age
4. The Terminator (18)
5. Surf’s Up (F) // any age
Enter the number of the film you wish to see: 10
That film number is invalid. Enter the number of the
film you wish to see:
It would be nice if you could improve your program to do this.
Before you go any further; perform the following:
3. Modify the Program.cs program so that it produces an error
message if the user gives a value which is out of range. One way
to do this is to repeat the test in the program. The first test
produces the message if the input is invalid and the other test
controls the loop.
4. If you are feeling ambitious you can take a look at the break
keyword and see if you can use this to make a version which
only does the test once. You can find the break keyword on
page 46 in the Yellow Book
7
Putting a Loop inside a Loop
The program we are writing should actually run continuously, in other words it should not
stop after it has run once. We can get this effect by putting a loop around the entire
program which will repeat it until the user says stop:
Another customer? (Y or N): Y
Welcome to Famous Players ...
This version of the program asks the user if they want to process another customer. If the
answer is Y the program will go round again. The program layout will look a bit like this:
string doWeGoRoundAgain;
do {
// code to process one film customer
Console.Write("Another customer? (Y or N):");
doWeGoRoundAgain = Console.ReadLine();
}
while (doWeGoRoundAgain == "Y");
It is perfectly OK for us to put loops inside loops, but remember to use indenting to make
it clear what is happening.
Before you go any further; perform the following:
5. Modify the Program.cs program so that it repeatedly processes
customers until the user says stop.
6. If you are feeling ambitious you can take a look at the
string.ToUpper() method that returns an upper case version
of a string. This would allow you to write a program that works
whether the user types Y or y.
Advanced Stuff – Handling Exceptions
The program you have written is nearly perfect, but not quite. If you are felling really
ambitious you can add exception handling to the program, so that the program behaves
correctly if the user does something like this:
Enter the number of the film you wish to see: bang
This problem is caused by the Parse method getting upset and
throwing an exception. You can find out how to deal with this by
looking at page 65 in the C# Yellow Book.
4) Sales Figure bar Chart
Write a program that ask’s the user to enter the sales for a single day for five separate stores.
With this data entered, your program should then create a bar chart, as shown below, where
each * character represents $100 in sales. Make sure your program only accepts non-negative
sales figures from the user.
8
Example Input/Output:
Enter today’s sales for store 1: 300
Enter today’s sales for store 2: 1200
Enter today’s sales for store 3: 1800
Enter today’s sales for store 4: 1550
Enter today’s sales for store 5: 1920
SALES BAR CHART
Store 1: ***
Store 2: ************
Store 3: ******************
Store 4: ***************
Store 5: *******************
5) Ro, Sham, Bo Game
Write a program that lets the user play the Game of Ro, Sham, Bo against the computer.
The program should work as follows:
1. When you start the program, a random number generator should be used to produce an
integer value between 1 and 3. Based on this generated value,
a. 1 represents the computer’s choice of rock
b. 2 represents paper
c. 3 represents scissors
2. The user should enter the choice by the string value “rock”, “paper”, or “scissors”
a. Please ensure a correct input value is entered. The casing of the text should not
matter.
3. The computer’s choice can now be displayed
4. Determine a winner based on the following rules
a. If one player selects rock and the other scissors, then rock wins
b. If one player selects paper and other rock, then paper wins
c. If one player selects scissors and the other paper, then scissors win
d. If both players select the same choice, the game is a draw
6) Largest Number of Vowels
Write a program that takes in a plain text file “words.txt” that contains a single word per line,
and determines what is the largest number of vowels in any of the words in the file; for
example, if your file contains:
Mark
Class
Onion
The output should be:
“The largest number of vowels in any one word is: 3”
9
7) Adding a ReadNumber method to Cinema Entry
We are now going to make our final improvements to the Cinema Entry program. We are
going to add a method to the program to make it easier to read numbers.
The method will accept a string and two integers. It will use the string as a prompt for the
user and reject any input values which are smaller than the minimum or larger than the
maximum. A programmer has written a method do this:
static int ReadNumber(string prompt, int min, int max)
{
int result = 0;
do
{
Console.Write(prompt);
string numberString = Console.ReadLine();
result = int.Parse(numberString);
if (result > max && result < max)
Console.WriteLine("Please enter a value in the range " +
min + " to " + max);
else
break;
}
while (true);
return result;
}
static void Main(string[] args)
{
int filmNumber = ReadNumber("Enter film number: ", 1, 6);
Console.WriteLine("Film number " + filmNumber + " chosen"); }
Above you can see the ReadNumber method and a Main method that calls it. Create a
copy of your finished version of Question 3, and enter the method in the Main method
into your new C# project.
Pausing the Display
The program above will work fine, but it will clear the screen as soon as it finishes, which
means that you might not see what you have entered. One way to solve this problem is to
read an empty line at the end of your program:
Console.WriteLine("Press return to exit");
Console.ReadLine();
These two statements display a message and then wait for the user to press enter, giving
us a chance to see what it did.
Testing the ReadNumber method
The ReadNumber method looks OK, but it might have a problem or two. If you run it with a
sample value in the range 1 to 6 it seems OK, but it doesn’t seem to notice invalid values:
Enter film number: -1
Film number -1 chosen
10
Press return to exit
A good set of test data is the values -1,0,1,3,5,6,7,1000. Make sure the program
works with all those values.
Finishing the program
Next we are going to explore how to use an array to store data, and how we can avoid
having to “hard wire” items into programs.
Welcome to Famous Players
We are presently showing:
1. Species (14)
2. Fight Club (14)
3. Stargate (PG) // any age
4. The Terminator (18)
5. Surf’s Up (F) // any age
Enter the number of the film you wish to see: 1
Enter your age: 12
Access denied – you are too young
Above you can see the menu from the cinema entry program. At the moment we are
creating the menu by writing out the individual film items:
Console.WriteLine(" 1. Species (14)");
Console.WriteLine(" 2. Fight Club (14)");
Console.WriteLine(" 3. Stargate (PG)");
Console.WriteLine(" 4. The Terminator (18)");
Console.WriteLine(" 5. Surf’s Up (F)");
This will work, but it means that every time the films change we have to make a new
program. What the program should do is read in the film names at the start, and then
display them for each customer. Later we can make the program read the names from a
file, or perhaps even a web feed.
Adding a film array
We are going to use an array of strings to hold the names of the films it will hold 5 names:
string[] filmNames = new string [5];
This statement creates an array which can hold five strings.
Reading in the film names
Now that we have an array we can read in some film names. The best way to do this is to
use a loop that goes round five times. We can use the control variable (the counter) in the
loop to access each element in the array in turn.
// Read in the film names
for (int i = 0; i < 5; i++)
11
{
int displayNumber = i + 1;
Console.Write("Enter the name of film number " + displayNumber + ": ");
filmNames[i] = Console.ReadLine();
}
This loop will read in the names. Note that C# will let us declare a control variable (in this
case the integer variable i) when the loop is set up. This variable will exist for the entire
loop body.
We know that the array is indexed from 0 (in other words the first
element in the array has the subscript of zero. However, users would
not expect to be counting from 0 in situations like this. Can you see
how the programmer has dealt with this?
Displaying the Menu
Once you have the array set up in the program you can use it to display the menu from
which the user will select the film that they want to see. You can use exactly the same for-
loop structure before (but you have to make a new for loop to display the menu).
Finding the selected film
The user will enter the number of the film that they want to see. However, they will start
counting at 1, whereas the film at the start of your array has the subscript 0. This means
that you will have to subtract 1 from the number they enter, to find the name of the film
that they have selected.
Handing the film age ratings
This seems to work well, but at the moment it looks like we have no way of handling the
age ratings of the films. Since that is what the program was created for, we need to sort
this out.
It turns out that the C# string type has a really useful method called EndsWith. You can
use it to see if a string ends with a particular piece of text. This is just what we want, since
the age rating is given right at the end of the film name. We will use a construction like
this:
if ( filmNames[chosenFilm].EndsWith("(14)") )
{
// The user has selected a film that is 14 rated
}
In the code snippet above the variable chosenFilm holds the number of the film that was
selected by the customer. This will be an integer in the range 0 to 4 (remember that
arrays are indexed from 0). The number was obtained by asking the user for the number
of the film they want to see, and then subtracting 1 from it.
12
The if condition looks for the string (14) on the end of the name, so that it can detect
films of that rating.
To keep is simple, create another if statement to respond if a film with (18) is selected.
Optional - Tidying Up
You can use the above techniques to make the ultimate Cinema Entry program. Here are
some thoughts to make it even better.
Use the Length property of the array to control your loops
At the moment you are counting up to 5 each time you work through the array. It turns out
that an array instance has a Length property that you can use. It tells the program how
many elements the array contains:
for (int i = 0; i < filmNames.Length; i++)
This means that if the size of the array changes (for example if more films are shown one
week) the program will still work correctly.
Allow the user to enter how many films are being shown
A C# array can be dynamically created, i.e. you can set the size of the array when the
program runs. This means that you could ask the user how many films that are being
shown and then make an array of the required size. This would also make your program
quicker to test, because you could enter the value 1 and just enter a single film name.
Add data tidying error checking
The technique of using EndsWidth to get the age ratings will work, but if the user doesn’t
type the rating value correctly, or adds a space on the end of the film name by mistake
the rating behaviour will not work as it should.
There is a method called Trim that you can use obtain a version of a string with all the
leading and trailing spaces removed:
trimmedName = enteredName.Trim();
The above statement sets the variable trimmedName (which must be a string) the value of
enteredName (which must also be a string) with all the leading and trailing spaces
removed.
You should also make sure that when the user enters the film names you check to make
sure that each has a sensible age rating. You will have to add some tests to do this. One
way would be to make a method called validateRating which accepts a string and
returns if the name is a valid one. Here is an empty version of the method to fill in. Note
the comments
/// <summary>
/// Validates the film name to make sure
13
/// the name ends with a valid rating string:
///
/// (14) (18) (PG) (G) or (F)
/// </summary>
/// <param name="filmName">name of the film to be checked</param>
/// <returns>true if the film name is valid</returns> static bool
validateRating(string filmName)
{
// need to fill in this code return false;
}
If you enter this method as above you will find that interesting things happen in Visual
Studio when you use it in your programs. If you want to add these comments to any
methods that you write you can produce the template by typing /// (three forward slashes)
in the editor just above the method.
