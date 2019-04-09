---
title: "Parking Lot Problem Extended"
excerpt: "Solved in Golang with data structures optimized for complexity"
header:
  teaser: assets/images/parkinglot_02.jpg
---

{% include toc %}

## Info

This project addresses an extended problem to that of the original [Parking Lot Problem](https://adaickalavan.github.io/portfolio/parking_lot_problem/).

## Problem Statement

In this extended problem, the carpark should accept three different types of vehicles, namely, motorcycle, car, and bus, requiring 1, 2, and 3 parking slots per vehicle, respectively.

| Type of vehicle   |  Number of parking slots needed per vehicle |
|:-----------------:|:-------------------------------------------:|
| Motorcycle        |                      1                      |
| Car               |                      2                      |
| Bus               |                      3                      |

All other rules, regulations, and operational requirements of the carpark remain the same as in the original problem.

An example in the interactive mode is as follows.

**Example: Interactive**

```
$ create_parking_lot 8
Created a parking lot with 8 slots
$ park KA-01-HH-1234 White motorcycle
Allocated slot number: 1
$ park KA-01-HH-9999 White car
Allocated slot number: 2
$ park KA-01-BB-0001 Black bus
Allocated slot number: 4
$ leave 1
Slot number 1 is free
$ park KA-01-HH-2701 Blue car
Allocated slot number: 7
$ leave 4
Slot number 4 is free
$ park KA-01-HH-7777 White car
Allocated slot number: 4
$ status
Slot No. Registration No  Colour  Type
2        KA-01-HH-9999    White   Car
4        KA-01-HH-7777    White   Car
7        KA-01-HH-2701    Blue    Car
$ park DL-12-AA-9999 White bus
Sorry, parking lot is full
$ registration_numbers_for_cars_with_colour White
KA-01-HH-9999, KA-01-HH-7777
$ slot_numbers_for_cars_with_colour White
2, 4
$ slot_number_for_registration_number KA-01-HH-2701
7
$ registration_numbers_for_cars_with_colour Green
Not found
$ slot_number_for_registration_number MH-04-AY-1111
Not found
$ exit
```

## Repository

Find the source code in the [repository](https://github.com/Adaickalavan/Parking-Lot-Problem-Extended).

## Learning Outcome

At the end of this project, we should be able to:

+ solve the Parking Lot problem with data structures optimized for complexity
+ utilize linked-list data structure in Go

## Project structure

The project structure is as follows:

```txt
project                               # folder containing all project files
├── bin                               # contains executable commands
│   ├── setup                         # contains commands to build/compile the Go code
│   └── parking_lot.exe               # .exe file for parking_lot generated by `go install` command
└── src                               # contains Go source files
    └── parking_lot                   # main folder
        ├── vendor                    # folder containing dependencies
        │   ├── minheap               # dependant package `minheap`  
        │   │   ├── item.go           # element of heap
        │   │   └── priorityQueue.go  # min heap implementation
        │   ├── pretty                # dependant package `pretty`  
        │   │   └── printer.go        # pretty prints array, slice, string
        │   └── sortedlist            # dependant package `sortedlist`  
        │       └── list.go           # sorted list implementation
        ├── vehicle.go                # element of carpark: motorcycle, car, and bus
        ├── carpark.go                # carpark struct and pointer receiver methods
        ├── carpark_test.go           # unit tests of the carpark.go code
        ├── main.go                   # main file of Go code
        ├── main_test.go              # functional test of the main code
        ├── inputFile.txt             # sample input file for testing
        └── inputInteractive.txt      # sample interactive input for testing
```

## Notes on solution

1. **Data structures**
   + A sorted linked-list data structure is used to maintain the list of sorted empty slots in ascending order, instead of a minheap data structure used in the original problem.