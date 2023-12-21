- Our syllabus contains techniques by ISTQB
- White box testing was mostly about going into the code and computing coverage testing, etc. But Black box testing does not need the source code, just the outputs
# Unit Testing
- is not pure black box testing approach
- Top down and Bottom up testing strategies from Pressman's book
# Integration Testing
- Integrated collection of modules are tested as a partial system
- The Integration plan specifies the order in which to the subsystems are selected for testing and integration, there are 2 types:
	1) Horizontal Integration Testing
	2) Vertical Integration Testing
# Horizontal Integration Testing:
## Bottom-up integration:
- need Drivers
## Top-down integration:
- need stubs
## Sandwich Testing:
- Combining bottom-up and top-down
## Big bang integration:
- Doesn't use stubs or drivers
- Every module is unit tested in isolation 
- After all of the modules are tested, they are all integrated together at once and tested
# Vertical Integration Testing:
- We do Acceptance test driven development
- We write several unit tests to make an acceptance test, then test that acceptance test
- Algorithm:
	- First a failing acceptance test is written
- used in Agile, by "user stories"
	- User stories are listed on a whiteboard
	- these are looked at to see what is done and what is not done
# Acceptance Testing
- Test on usability by a user
## Alpha testing
- done in the development organization
## Beta testing
- performed by group of friendly customers
- Here, for example, it shows that the app is in beta testing (see the info part in the image below)
![[Pasted image 20231212150757.png|200]]
# Black Box Test Design Techniques:
- There are 5 techniques defined in BS 7925-2, asked by ISTQB
	1) Equivalence Partitioning
	2) Boundary Value Analysis (BVA)
	3) Decision Table
	4) State Transition Testing
	5) Use case Testing
## 1) Equivalence partitioning
- separate/divide the input domain into different partitions
- select at least 1 value from each partition, and test them
>[!info] Idea of Equivalence Partitioning:
>- If a value from one partition works, then all other values from this partition will work
## 2) Boundary Value Analysis (BVA)
- It is an extension of Equivalence partitioning
- Apply same process as Equivalence partitioning, but choose values that are at the boundary of the partitions (except positive and negative infinity)
- Boundary Value:
	- is an input value which is on the edge of an equivalence partition
>[!warning]
>- It may make sense to do only BVA, as it is an extension of Equivalence Partitioning, but that is **not the case**, becuase if there is an error, you may not know whether, error was in the boundary value or the whole partition.
>- So it is better to do both tests
## 3) Decision Table
- We will have a set of $n$ (where $n$ is the number of options) options/statements/situations that may be true or false.
- We will make a truth table that will have $2^n$ columns
- Each cell in the Decision Table will be true or false depending on the combination of the statements
- This is used to *generate* test cases
## 4) State Transition Testing
- We have different states
	- each state has a "start state" and "end state"
- We change states through an "event" called a "transition"
- after making the state transition diagram, will have to make a table to show all combinations of valid and invalid transitions
- for example:

| States                           | insert card      | valid pin | invalid pin |
| --------------------------------- | ---------------- | --------- | ----------- |
| S1) start state                   | S2               | -         | -           |
| S2) Wait for pin                  | -                | S6        | S3          |
| S3) 1st try invalid               | -                | S6        | S4          |
| S4) 2nd try invalid               | -                | S6        | S5          |
| S5) 3rd try invalid | -                | -         | S7          |
| S6) Access account                | -                | ?         | ?           |
| S7) eat card                      | S1(for new card) | -         | -            |

>[!info] Extra Information
>The idea of state transition diagrams came from finite state machines, which you can check out in [this link](https://en.wikipedia.org/wiki/Finite-state_machine#Representations) 
## 5) Use case Testing
- Test cases are designed to execute scenarios of use cases
- We have a test of the success scenario and one test for each alternative flow scenario