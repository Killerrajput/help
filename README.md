1 a)
def countNow(PLACES):
    # Loop through the dictionary
    for place in PLACES.values():
        # Check if the place name is longer than 5 characters
        if len(place) > 5:
            # Print the name in uppercase
            print(place.upper(), end=' ')
            
# Example usage:
PLACES = {1: "Delhi", 2: "London", 3: "Paris", 4: "New York", 5: "Doha"}
countNow(PLACES)

b)
def lenWords(STRING):
    # Split the string into words
    words = STRING.split()
    # Create a tuple with the length of each word
    lengths = tuple(len(word) for word in words)
    return lengths

# Example usage:
STRING = "Come let us have some fun"
result = lenWords(STRING)
print(result)

2 a)
def display_lines_starting_with_you(filename):
    try:
        with open(filename, 'r') as file:
            for line in file:
                # Strip leading/trailing whitespace and check if the line starts with 'You'
                if line.strip().startswith('You'):
                    print(line.strip())
    except FileNotFoundError:
        print(f"The file {filename} does not exist.")
    except IOError:
        print(f"An error occurred while reading the file {filename}.")

# Example usage:
display_lines_starting_with_you('Alpha.txt')

b)
def vowelCount(filename):
    vowels = 'aeiouAEIOU'  # Define vowels
    count = 0  # Initialize the count of vowels

    try:
        with open(filename, 'r') as file:
            for line in file:
                # Count vowels in the current line and add to total count
                count += sum(1 for char in line if char in vowels)
        print(f"Number of vowels in the file '{filename}': {count}")
    except FileNotFoundError:
        print(f"The file {filename} does not exist.")
    except IOError:
        print(f"An error occurred while reading the file {filename}.")

# Example usage:
vowelCount('Poem.txt')

3 a)
def LongLines(filename):
    try:
        with open(filename, 'r') as file:
            for line in file:
                # Split the line into words and count them
                words = line.split()
                if len(words) >= 10:
                    print(line.strip())
    except FileNotFoundError:
        print(f"The file {filename} does not exist.")
    except IOError:
        print(f"An error occurred while reading the file {filename}.")

# Example usage:
LongLines('LINES.TXT')

b)
import re

def countDwords(filename):
    count = 0
    # Regular expression pattern to match words ending with a digit
    pattern = re.compile(r'\b\w*\d\b')

    try:
        with open(filename, 'r') as file:
            for line in file:
                # Find all words in the line that end with a digit
                words = pattern.findall(line)
                count += len(words)

        print(f"Number of words ending with a digit in the file '{filename}': {count}")
    except FileNotFoundError:
        print(f"The file {filename} does not exist.")
    except IOError:
        print(f"An error occurred while reading the file {filename}.")

# Example usage:
countDwords('Details.txt')

4 a)
class HotelStack:
    def __init__(self):
        self.stack = []

    def Push_Cust(self, records):
        # Push customer names of those staying in 'Delux' room type
        for record in records:
            customer_name, room_type = record
            if room_type == 'Delux':
                self.stack.append(customer_name)

    def Pop_Cust(self):
        # Pop the names of customers from the stack and display them
        if not self.stack:
            print("Underflow")
        else:
            while self.stack:
                print(self.stack.pop())

# Example usage:
hotel = HotelStack()

# List of customer records
records = [
    ["Siddarth", "Delux"],
    ["Rahul", "Standard"],
    ["Jerry", "Delux"]
]

# Push customers staying in 'Delux' room type onto the stack
hotel.Push_Cust(records)

# Pop and display customer names from the stack
hotel.Pop_Cust()

b)
class VehicleStack:
    def __init__(self):
        self.stack = []

    def Push(self, vehicle_dict):
        # Normalize 'TATA' case variations
        tata_makers = {'tata', 'tata', 'tata', 'tata', 'tata', 'tata'}
        for car_name, maker in vehicle_dict.items():
            if maker.lower() in tata_makers:
                self.stack.append(car_name)

    def DisplayStack(self):
        # Display the stack content
        if not self.stack:
            print("Stack is empty.")
        else:
            for car in self.stack:
                print(car)

# Example usage:
vehicle_stack = VehicleStack()

# Dictionary containing vehicle details
vehicles = {
    "Santro": "Hyundai",
    "Nexon": "TATA",
    "Safari": "Tata"
}

# Push cars manufactured by 'TATA' onto the stack
vehicle_stack.Push(vehicles)

# Display the stack content
vehicle_stack.DisplayStack()


5) a)
Closing a file after use is important because it frees up system resources that are being used by the file. When a file is open, the operating system allocates memory and other resources to the file, which can potentially impact the performance of the system if too many files are open at the same time.
5 b)
import csv

def Add_Book():
    # Input book details from the user
    book_id = input("Enter Book ID: ")
    book_name = input("Enter Book Name: ")
    publisher = input("Enter Publisher: ")
    
    # Open the CSV file in append mode
    with open('Book.csv', 'a', newline='') as file:
        writer = csv.writer(file)
        # Write the book details to the CSV file
        writer.writerow([book_id, book_name, publisher])
    print("Book added successfully.")

def Search_Book():
    publisher_to_search = input("Enter Publisher Name to search: ").strip()
    count = 0
    
    try:
        # Open the CSV file in read mode
        with open('Book.csv', 'r') as file:
            reader = csv.reader(file)
            # Iterate through the rows and count books with the given publisher
            for row in reader:
                if row and row[2].strip().lower() == publisher_to_search.lower():
                    count += 1
        print(f"Number of books published by {publisher_to_search}: {count}")
    except FileNotFoundError:
        print("The file 'Book.csv' does not exist.")

# Example usage:
# Add books to the CSV file
Add_Book()

# Search for books by publisher
Search_Book()

6 a)
In CSV files, fields are always separated by commas. In TXT files, fields can be separated with a comma, semicolon, or tab

b)
import csv

def COURIER_ADD():
    # Input courier details from the user
    cid = input("Enter Courier ID: ")
    s_name = input("Enter Sender Name: ")
    source = input("Enter Source Address: ")
    destination = input("Enter Destination Address: ")
    
    # Open the CSV file in append mode
    with open('courier.csv', 'a', newline='') as file:
        writer = csv.writer(file)
        # Write the courier details to the CSV file
        writer.writerow([cid, s_name, source, destination])
    print("Courier details added successfully.")

def COURIER_SEARCH():
    destination_to_search = input("Enter Destination Address to search: ").strip()
    
    try:
        # Open the CSV file in read mode
        with open('courier.csv', 'r') as file:
            reader = csv.reader(file)
            # Initialize a flag to check if any records are found
            found = False
            # Iterate through the rows and display records with the given destination
            for row in reader:
                if row and row[3].strip().lower() == destination_to_search.lower():
                    print(f"Courier ID: {row[0]}, Sender Name: {row[1]}, Source Address: {row[2]}, Destination Address: {row[3]}")
                    found = True
            if not found:
                print(f"No records found for destination: {destination_to_search}")
    except FileNotFoundError:
        print("The file 'courier.csv' does not exist.")

# Example usage:
# Add courier details to the CSV file
COURIER_ADD()

# Search for couriers by destination
COURIER_SEARCH()



