# Modern Java Practice Problems

## Getting Started

- Program that reads command-line arguments and display it on the console
- Program that simulates the roll of a dice
- Program that generates 10 random double values between 10 and 100 (for example, stock prices of 10 companies)
- Express each of the following phrases as strings:
  - They’ll hibernate during the winter.
  - “Absolutely not,” he said.
  - “He said, ‘Absolutely not,’” recalled Mel.
  - hydrogen sulfide
  - left\right

## Methods

- Program that calls a function that has one parameter, a number, and returns that number tripled.
- Program that calls a function that has two parameters, both of which are numbers, and returns the absolute value of the difference of the two
- Program that calls a function that has one parameter, a distance in kilometers, and returns the distance in miles. (There are 1.6 kilometers P)
- Program that calls a function that has three parameters, grades between 0 and 100 inclusive, and returns the average of those grades.
- Program that calls a function that has four parameters, all of them grades between 0 and 100 inclusive, and returns the average of the best 3 grades
- Program that calls a function `def repeat(s: str, n: int) -> str` that returns a string 's' repeated 'n' times; if 'n' is negative, return the empty string
- Write a `convert_temperatures(t, source, target)` function to convert temperature 't' from 'source' units to 'target' units, where source and target are each one of "Kelvin", "Celsius", "Fahrenheit", "Rankine", "Delisle", "Newton", "Reaumur", and "Romer" units.
  Hint: Use [Wikipedia](https://en.wikipedia.org/wiki/Conversion_of_units_of_temperature#Comparison_of_temperature_scales)
- Variable 's' refers to `' yes '`. Write a method when called with 's' as its argument would return 'yes'
- Write a program that calls a function that produces the following:
  - A copy of 'boolean' capitalized
  - The first occurrence of '2' in 'CO2 H2O'
  - The second occurrence of '2' in 'CO2 H2O'
  - True if and only if 'Boolean' begins lowercase
  - A copy of "MoNDaY" converted to lowercase and then capitalized
  - A copy of " Monday" with the leading whitespace removed

## Collections

- Variable kingdoms refers to the list `['Bacteria', 'Protozoa', 'Chromista', 'Plantae', 'Fungi', 'Animalia']`. Using kingdoms and either slicing or indexing with positive indices, write expressions that produce the following:
  - The first item of kingdoms
  - The last item of kingdoms
  - The list `['Bacteria', 'Protozoa', 'Chromista']`
  - The list `['Chromista', 'Plantae', 'Fungi']`
  - The list `['Fungi', 'Animalia']`
  - The empty list
- Write a program `def same_first_last(L: list) -> bool` that returns True if and only if first item of the list is the same as the last

## Loop

- In this exercise, you’ll create a nested list and then write code that performs operations on that list.
  - Create a nested list where each element of the outer list contains the atomic number and atomic weight for an alkaline earth metal. The values are beryllium (4 and 9.012), magnesium (12 and 24.305), cal- cium (20 and 40.078), strontium (38 and 87.62), barium (56 and 137.327), and radium (88 and 226). Assign the list to variable alkaline_earth_metals.
  - Write a for loop to print all the values in alkaline_earth_metals, with the atomic number and atomic weight for each alkaline earth metal on a different line.
  - Write a for loop to create a new list called number_and_weight that contains the elements of alkaline_earth_metals in the same order but not nested.
- Using nested for loops, print a right triangle of the character T on the screen where the triangle is one character wide at its narrowest point and seven characters wide at its widest point:

```
T
TT
TTT
TTTT
TTTTT
TTTTTT
TTTTTTT
```

- Using nested for loops, print the triangle described in the previous exercise with its hypotenuse on the left side:

```
      T
     TT
    TTT
   TTTT
  TTTTT
 TTTTTT
TTTTTTT
```

## Date/Time

- Program that displays current date and time in the current timezone
- Program that displays current date and time in a timezone passed as a paramter
- Program that calls a function (weeks_elapsed) that takes two parameters, two days in the same year and returns the full weeks that have elapsed between the two days
- Program that calculates the number of days, hours, mins and seconds between two date/time passed as a paramter

## Currency

- Program that displays money value using locale of different countries
- Program that displays money value in different currencies using locale of different countries

## IO

- Program that prompts users for a set of values and displays it on the console
- Program that reads from a file and displays it on the console
- Program that reads a CSV file and loads it into an array of objects
- Program that creates and appends to a CSV file
- Program that reads environment variables
- Write a program that makes a backup of a file. Your program should prompt the user for the name of the file to copy and then write a new file with the same contents but with `.bak` as the file extension.
- Suppose the file `alkaline_metals.txt` contains the name, atomic number, and atomic weight of the alkaline earth metals. Write a program to read the contents of `alkaline_metals.txt` and store it in a list of lists, with each inner list containing the name, atomic number, and atomic weight for an element:

```
beryllium 4 9.012
magnesium 12 24.305
calcium 20 20.078
strontium 38 87.62
barium 56 137.327
radium 88 226
```

- Program that reads backward through a file

## Systems Programming

- Program that runs a process on the operating system and reads its output
- Program that traverses a folder structure and prints file and folder name with additional file/folder attributes

## Simple Software

- Program that implements Rock, Paper and Scissors game where user's input is received from the Console
- After doing a series of experiments, you have compiled a dictionary showing the probability of detecting certain kinds of subatomic particles. The particles’ names are the dictionary’s keys, and the probabilities are the values: `{'neutron': 0.55, 'proton': 0.21, 'meson': 0.03, 'muon': 0.07, 'neutrino': 0.14}`. Write a function that takes a single dictionary of this kind as input and returns the particle that is least likely to be observed. Given the dictionary shown earlier, for example, the function would return `'meson'`.
- A sparse vector is a vector whose entries are almost all zero, like `[1, 0, 0, 0, 0, 0, 3, 0, 0, 0]`. Storing all those zeros in a list wastes memory, so program- mers often use dictionaries instead to keep track of just the nonzero entries. For example, the vector shown earlier would be represented as `{0:1, 6:3}`, because the vector it is meant to represent has the value 1 at index 0 and the value 3 at index 6.

  - The sum of two vectors is just the element-wise sum of their elements. For example, the sum of `[1, 2, 3]` and `[4, 5, 6]` is `[5, 7, 9]`. Write a function called sparse_add that takes two sparse vectors stored as dictionaries and returns a new dictionary representing their sum.
  - The dot product of two vectors is the sum of the products of corresponding elements. For example, the dot product of `[1, 2, 3]` and `[4, 5, 6]` is `4+10+18`, or `32`. Write another function called sparse_dot that calculates the dot product of two sparse vectors.

  ## Enterprise Software

- Create Web App
  - With AuthC
- Create REST API
  - Responds with JSON Payload
  - With CORS enabled
- Create a Serverless App
  - Responds to an Event
  - Writes the event data to S3
- Create CLI
- Backend Integrations
  - Interacts with a REST API
      - JSON Payload
      - GET, POST, PUT, DELETE
  - Interacts with PostgreSQL
  - Interacts with MongoDB
  - Interacts with Redis
  - Interacts with RabbitMQ
  - Interacts with Kafka

## Conceptual ones

- Program that calls a method that shows the binary value of an integer

## Other Sources

- Exercises in
  - _Core Java SE 9 for the Impatient_ chapters
  - _Java How to Program Early Objects 10th Edition_ chapters
  - _Exercises for Programmers_ chapters
  - _Mazes for Programmers_ chapters
- [Coding Bat](https://codingbat.com/java)
- [CodeGym](https://codegym.cc/quests/lectures/questsyntax.level00.lecture00)
