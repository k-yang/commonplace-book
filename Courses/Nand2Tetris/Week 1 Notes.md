HOW - implementation
WHAT - abstraction/interface

Who worries about the "how"? Someone else, or you, earlier, or later.

# Boolean Logic
Associative, Commutative, Distributive, De Morgan's Law


# Boolean Function Synthesis
Go from truth table to a boolean function
Disjunctive Normal Form
Any boolean function can be represented by an expression using NAND operations

# Logic Gates
Gate logic: implements boolean functions using logic gates
Logic gates: chips that delivers well defined functionality

# Hardware Description Language
Static textual description of the gate diagram
HDL is a functional declarative language

# Hardware Simulation
Simulation options
- interactive
- script based
- output and compare files

Behavioural simulation allows a chip to be implemented in a high level language to generate the compare file

# Multi-Bit Buses
It's conceptually convenient to think of a group of bits as a single entity, termed "bus"
Buses can be broken up into sub-buses

## Multiplexor
Selects between multiple inputs based on selection inputs

## Demultiplexor
Acts as the inverse of a multiplexor
Distributes a single input into one of possible output channels, depending on the selection input

Muxes and demuxes can be used by multiple communication channels to share a single communication channel

