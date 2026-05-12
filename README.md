# Gym Meal Machine 🏋️

A Java-based vending machine simulator developed for BBM104: Introduction to Programming Laboratory II at Hacettepe University.

## About the Project

This project simulates a **Gym Meal Machine (GMM)** — a vending machine designed for athletes and fitness enthusiasts. Users can purchase meals based on their nutritional preferences (protein, carbohydrate, fat, or calorie content) or directly by slot number.

The machine has **6 rows and 4 columns** (24 slots total), and each slot can hold up to **10 units** of the same product.

---

## Features

- Loads products from a file into a 6x4 slot machine (row by row, left to right)
- Calculates calorie values using the Atwater system
- Accepts purchases by nutritional value (PROTEIN, CARB, FAT, CALORIE) or slot NUMBER
- Validates money — accepts only: 1, 5, 10, 20, 50, 100, 200 TL
- Returns correct change after each purchase
- Handles edge cases: full machine, empty slots, insufficient funds, invalid money

---

## How to Run

    javac *.java
    java -cp . Main Product_1.txt Purchase_1.txt GMMOutput.txt
    
Three arguments must be provided in this order: product file, purchase file, output file. Sample input files are provided as `Product_1.txt` / `Product_2.txt` / `Product_3.txt` and `Purchase_1.txt` / `Purchase_2.txt` / `Purchase_3.txt`.

---

## Calorie Calculation

Since Product.txt does not include calorie values, the program calculates them using the Atwater system:

    calorie (kcal) = 4 x protein (g) + 4 x carbohydrate (g) + 9 x fat (g)

---

## Loading the Machine

- Products are loaded row by row, left to right
- If a slot already contains that product and is not full, it is used first
- If a slot is full, the next available empty slot is used
- Each slot holds a maximum of 10 units
- If all slots are full, an info message is printed and loading stops

---

## Purchasing

- Members select by nutritional value (PROTEIN, CARB, FAT, CALORIE) or directly by slot NUMBER
- When selecting by nutritional value, the first product within +-5 range of the requested value is returned
- If there is a problem (empty slot, insufficient money, invalid input), money is returned and an info message is printed

---

## Input / Output Files

### Product.txt

Each line contains one product in the following format:

    Name[TAB]Price[TAB]Protein[SPACE]Carbohydrate[SPACE]Fat

Example:

    Chicken Wrap    18    32 45 28
    Beef Sandwich   20    33 28 27
    Fried Rice      15    11 90 8.2

---

### Purchase.txt

Each line represents one purchase attempt:

    Type[TAB]Money_1 ... Money_n[TAB]Choice[TAB]Value

Example:

    CASH    5 10      PROTEIN    30
    CASH    20 1 1 1  NUMBER     5
    CASH    20 10     CARB       30

---

### GMMOutput.txt

The output file contains:

1. Machine state after loading. Each slot is shown as:

    ProductName(calorie, quantity)___

   Empty slots are shown as:

    ___(0, 0)___

2. Each purchase transaction, showing:
   - INPUT:    the purchase request
   - PURCHASE: the product dispensed
   - RETURN:   change returned
   - INFO:     any error or informational message

3. Final machine state after all purchases

Example transaction output:

    INPUT: CASH    20 10    CARB    30
    PURCHASE: You have bought one Beef Sandwich
    RETURN: Returning your change: 10 TL

---

## Technologies

- Java 8
- Object-Oriented Programming (Classes, Objects, Encapsulation)

---

## Course

BBM104 — Introduction to Programming Laboratory II
Hacettepe University, Spring 2024
