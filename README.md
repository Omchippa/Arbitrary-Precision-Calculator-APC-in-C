# Arbitrary-Precision-Calculator-APC-in-C
Arbitrary Precision Calculator in C that adds, subtracts, multiplies, and divides very large numbers using doubly linked lists.
# 🧮 Arbitrary Precision Calculator (APC) in C

A command-line calculator that performs **addition, subtraction, multiplication, and division on very large numbers** that don't fit in normal C data types like `int` or `long`. Each number is stored digit by digit in a **doubly linked list**.

---

## ✨ Features

- Works with numbers of any length (limited only by memory)
- Supports `+`, `-`, `x`, and `/`
- Handles negative numbers
- Dynamic memory allocation, with all nodes freed after use

---

## 📁 Project Structure

```
APC/
├── calculator.c      # main(): argument validation, sign handling, operator selection
├── APC_header.h      # Node structure, enums, function prototypes
├── inserting_fun.c   # Insert digits into lists, free memory, compare, print
├── add_fun.c         # Addition
├── sub_fun.c         # Subtraction
├── mul_fun.c         # Multiplication
├── division_fun.c    # Division
└── makefile          # Build instructions
```

---

## 🚀 How to Run

### Build

```bash
make
```

or compile manually:

```bash
gcc calculator.c inserting_fun.c add_fun.c sub_fun.c mul_fun.c division_fun.c -o result.exe
```

### Usage

```bash
./result.exe <operand1> <operator> <operand2>
```

Use `x` for multiplication (the `*` symbol is treated as a wildcard by the shell).

### Examples

```bash
./result.exe 123456789123456789 + 987654321987654321
./result.exe 500 - 123
./result.exe 99999999999 x 99999999999
./result.exe 100 / 5
./result.exe -25 + 10
```

---

## 🧠 How It Works

### Data Structure

Each digit of a number is stored in one node of a doubly linked list:

```
NULL <- [1] <-> [2] <-> [3] -> NULL
        head              tail
```

Calculations start from the **tail** (the last digit) and move toward the **head**, just like pen-and-paper math.

### Operations

| Operation | Method |
|---|---|
| **Addition** | Add digit by digit from the tail, keep a carry, and insert each result digit at the front of the result list |
| **Subtraction** | Subtract digit by digit; if a digit is smaller, borrow from the previous node. The bigger number is always placed first |
| **Multiplication** | Multiply by each digit of the second number, shift each partial result with trailing zeros, and add all the partial results |
| **Division** | Repeatedly subtract the divisor from the dividend and count the subtractions. The count is the quotient |

### Sign Handling

The signs are removed before storing digits. The program decides the final operator and the sign of the result using the signs of both inputs and which number is bigger. For example, `-5 + 3` becomes a subtraction and the result is `-2`.

---

## 🛠️ Tech Stack & Tools

| Category | Details |
|---|---|
| **Language** | C |
| **Compiler** | GCC |
| **Build Tool** | Make |
| **Data Structure** | Doubly linked list |
| **Concepts** | Dynamic memory allocation, pointers, structures, enums, modular programming |
| **Libraries** | `stdio.h`, `string.h`, `stdlib.h` |

---

## ⚠️ Limitations

- Only integers are supported, and division returns the quotient only
- Division uses repeated subtraction, so it is slow for very large quotients
- Division by zero is not handled
- Non-numeric input is not validated



## 👤 Author

**Om Chippa**
