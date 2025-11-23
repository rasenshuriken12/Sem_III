| Computer Architecture | Computer Organization |
|--|--|
| Architecture (CA) is the `What`. | Organization (CO) is the `How`. |  
| It's the functional behavior of the computer from the programmer's point of view. | It's how those architectural features are physically implemented in the hardware. |
|  It includes the instruction set, addressing modes, and data types. | It deals with how components like the CPU, memory, and I/O are connected and work together. |

# Von Neumann Architecture 

1. Stored-Program Concept
- Both data and instructions are stored in the same main memory (RAM).

![images](https://github.com/DeviprasadShetty9833/Sem_III_Notes/blob/23aef3064bc453f481943a05e02ed83c772249b0/DLCOA/assets/VonNeumann.png)

## Components
- Central Processing Unit (CPU): The brain of the computer. It consists of:
  - Arithmetic Logic Unit (ALU): Performs all mathematical calculations (add, subtract) and logical operations (AND, OR, NOT).
  - Control Unit (CU): Directs the operation of the processor. It interprets instructions and coordinates the activities of all other hardware components.
  - Registers: Small, high-speed memory locations inside the CPU for temporary storage of data, instructions, and addresses (e.g., Program Counter, Instruction Register, Accumulator).
- Memory Unit (Main Memory/RAM): A single, unified storage space for both data and instructions. Each location in memory has a unique address.
- Input/Output (I/O) Systems: Allow the computer to communicate with the external world (e.g., keyboard, mouse, monitor, printer).
- System Bus: A single communication path that connects all the major components.

## Communication between CPU & memory
- Access data or instructions in memory - CPU -> memory location -> Address bus
- CPU -> read/write signal -> Control bus
- For Writing - CPU -> data thru data bus -> [Memory Controller] -> Memory Location    ...(Opp for Reading)













