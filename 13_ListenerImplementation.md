## Assignment on Listener Threads: Detailed Notes 📝

### Overview 🌐

- The assignment involves creating a small application called `listener_main.exe`.
- This application listens to multiple events concurrently using listener threads.

### Features 🎯

1. **Two Packet Listener Threads**: 
    - Listens on IP address `127.0.0.1` and UDP ports `3000` and `3001`.
2. **Packet Receive Function**: 
    - Processes packets received from the outside world.
3. **User Interaction Thread**: 
    - Receives inputs from the user and acts upon them.

### Technical Details 🛠️

- **Socket Programming Required**: You need basic socket programming skills.
- **Provided Libraries**: `network_utils.c` and `network_utils.h` include two important APIs:
  - `UDP_server_create_and_start`
  - `UDP_send_message`

### Testing 🧪

- A separate executable called `UDP_sender.exe` is provided.
- This can be used to send UDP packets to `listener_main.exe` for testing.

### Steps to Complete 📝

1. Write the `listener_main.exe` application.
2. Add logic to the packet receive function to print received packet size.
3. Launch the user interaction thread to take user inputs.

### Directory 📂

- All code examples and files can be found under: `Assignments/Listener_Threads`.

---

## Interview Questions and Answers 🎤

#### 1. What is the purpose of `listener_main.exe`?

   - The `listener_main.exe` is a small application designed to listen to multiple events at the same time through specialized listener threads.

#### 2. How many listener threads are involved and what do they do?

   - Two packet listener threads are involved that listen on the IP address `127.0.0.1` and UDP ports `3000` and `3001`.

#### 3. Explain the role of the packet receive function.

   - The packet receive function is responsible for processing packets that come from the outside world. It's invoked by the listener threads to handle the received packets.

#### 4. How does `listener_main.exe` interact with the user?

   - A separate thread, called the user interaction thread, is responsible for receiving inputs from the user and acting upon them.

#### 5. What are the key libraries or APIs used in this assignment?

   - Two key APIs are used: `UDP_server_create_and_start` and `UDP_send_message`. These are found in the provided `network_utils.c` and `network_utils.h` libraries.

#### 6. How do you test whether `listener_main.exe` is working as expected?

   - The `UDP_sender.exe` executable can be used to send UDP packets to `listener_main.exe`, allowing you to test whether it's listening and processing packets correctly.

---

Feel free to refer back to these notes for quick revision before interviews. Good luck! 🍀

## Multithreading Bible: Event Listeners - Detailed Notes 📝

### Introduction 🌟

- The discussion revolves around a directory named `multithreading Bible/event listeners`.
- This directory contains various files including `network_utils.h` which plays a crucial role.

### Key Files 📂

1. **network_utils.h**: 
    - Provided file containing APIs and code related to networking.

### Main API 🛠️

- **UDP_server_create_and_start**: 
    - This API is used for creating a listener thread that listens on a given IP address and port number.
    - The API takes three arguments:
        1. IP address
        2. Port number
        3. Function pointer (to pump packets back into the main application)
    - Returns a pointer to the created listener thread.

### Compilation & Execution ⚙️

- A shell script is available to compile all files.
- Running this compilation script generates the executable `listener_main.exe`.

### Working 🎛️

1. **Listener Threads**:
    - Two listener threads get created.
    - They listen on IP `127.0.0.1` and UDP ports `3000` and `3001`.
  
2. **Testing**:
    - Another executable `udp_standard.exe` is available for testing.
    - This can send packets to any of the listener threads based on the port number specified.

3. **Flexibility**: 
    - The application allows the creation of as many listener threads as needed.

### File Implementing Main App 📚

- `Listener Main.c` contains the implementation of the main application.
- The next lecture will delve into the implementation of this file.

---

## Interview Questions and Answers 🎤

#### 1. Can you describe what the `UDP_server_create_and_start` API does?

   - The API is used for creating a listener thread that starts listening on a specified IP address and port number. When the listener application receives packets, it invokes a function passed as an argument to process these packets.

#### 2. How do you compile all the files in the `multithreading Bible/event listeners` directory?

   - There is a shell script in the directory that can be run to compile all files, creating the executable `listener_main.exe`.

#### 3. What are the responsibilities of the listener threads created by the `listener_main.exe`?

   - The listener threads listen on IP address `127.0.0.1` and UDP port numbers `3000` and `3001`. They capture incoming packets and invoke a specified function to process those packets.

#### 4. How can you test the functionality of `listener_main.exe`?

   - You can use the `udp_standard.exe` executable to send packets to `listener_main.exe`. This helps in verifying if the listener threads are correctly receiving and processing packets.

#### 5. Can the application handle more than two listener threads?

   - Yes, the application provides the flexibility to create as many listener threads as needed.

#### 6. What does the `network_utils.h` file provide?

   - It provides the networking-related APIs and code, including the crucial `UDP_server_create_and_start` API.

#### 7. Which file contains the main application logic?

   - The main application logic resides in `Listener Main.c`.

---

Feel free to revisit these notes for quick interview preparation. Best of luck! 🍀

## Listener Main.exe Implementation - Detailed Notes 📝

### File Context 🗂️

- The discussion takes place in the file `listener Main.c`.
- This is where the main application, `listener Main.exe`, is implemented.

### Variables and Handles 🚀

- Two variables, `listener1` and `listener2`, of pointer types, are created.
- These variables represent two listener threads.

### Creating Listener Threads 🧵

1. **First Listener Thread**
    - Utilizes the API `server_create_and_start()`.
    - Arguments to the API:
        1. IP Address: `127.0.0.1`
        2. Port number: `3000`
        3. Function pointer to `packet_receive_function`.

2. **Second Listener Thread**
    - Similar to the first but listens on port number `3001`.

### Packet Receive Function 📦

- Function owned by the application, invoked by listener threads.
- Simply prints out a message indicating the packet that is received and its size.

### Other Important Points 📍

- Understanding of the API `UDP_server_create_and_start` requires basic UDP programming knowledge.
- Threads should terminate using `pthread_exit`.

### Compilation and Testing 🛠️

- Compilation creates the executable `listener Main.exe`.
- The program will listen on port numbers `3000` and `3001`.
- Use `UDP_standard.exe` for testing.

---

## Interview Questions and Answers 🎤

#### 1. What are `listener1` and `listener2` variables in the `listener Main.c` file used for?

  - These are pointer variables that represent the two listener threads which the main application creates.

#### 2. How does the application create the listener threads?

  - The application uses the API `server_create_and_start()` to create listener threads. It passes the IP address, port number, and a function pointer to this API.

#### 3. Can you explain the role of the `packet_receive_function` in this context?

  - The function is invoked by the listener threads when they receive packets from the network. It simply prints the received packet and its size to indicate the handover of the packet to the main application for processing.

#### 4. Why is understanding basic UDP programming essential for working with `UDP_server_create_and_start` API?

  - Understanding basic UDP programming is essential as the API encapsulates socket programming concepts and sets up a UDP server that listens for incoming packets.

#### 5. What's the importance of using `pthread_exit` in the program?

  - Using `pthread_exit` ensures that only the main thread terminates, allowing the other threads created by the application to continue running.

#### 6. How can you test the `listener Main.exe` application after compilation?

  - After compiling, you can test the application using the `UDP_standard.exe` executable to send packets to the ports `3000` and `3001` on which the application is listening.

#### 7. Why isn't complex logic needed in the `packet_receive_function`?

  - Complex logic isn't needed because the purpose of the function is merely to demonstrate the handover of the packet from the listener threads to the main application for processing.

---

These notes should serve as a comprehensive resource for your interview preparation. Good luck! 🍀

## Network Utils.c Implementation - Detailed Notes 📝

### File Context 🗂️

- Discussion takes place in the file `network_utils.c`.
- This file implements all networking logic, particularly the creation of listener threads.

### Function for Listener Threads 🧵

- The function of focus is used in the main program to create listener threads.
- Required knowledge: basic socket programming.

### Function Signature 📚

- **API Name**: Not specified but let's call it `create_packet_listener_thread`.
- **Arguments**:
    1. IP Address
    2. Port number
    3. Callback function for packet arrival.

### Steps to Create Listener Thread 🛠️

1. **Thread Creation**
    - The function initially creates a thread in detached mode.
    
2. **Thread Argument Package**
    - Memory allocation for a custom data structure called `thread_argument_package`.
    - This package includes:
        - IP Address
        - Port Number
        - Pointer to the receive function.

3. **Networking Logic**
    - Socket is created and bound to the IP address and port number.
    - Infinite loop listens for packets.
    - Blocking API `receive_from` is used to wait for packet arrival.
    
4. **Receive Buffer**
    - A buffer is used to store incoming packets.
    
5. **Callback Function**
    - Once a packet is received, a pre-defined function is invoked to notify the main application.

### Assignment: Thread Cancellation 📝

- No thread cancellation logic is present in the current code.
- Assignment is to make the listener thread cancelable.

---

## Interview Questions and Answers 🎤

#### 1. What is the main role of the file `network_utils.c`?

  - This file is responsible for implementing all the networking logic, including the creation of listener threads.
  
#### 2. What are the key parameters needed to create a packet listener thread?

  - The API requires an IP address, a port number, and a callback function to be passed as arguments.
  
#### 3. What does the custom data structure `thread_argument_package` contain?

  - This custom data structure includes the IP address, port number, and a pointer to the receive function. It's used to pack all necessary arguments for thread creation.

#### 4. Can you explain the purpose of the `receive_from` API in this context?

  - The `receive_from` API is a blocking function that waits for packets to arrive on the UDP socket. It is called within an infinite loop by the packet listener thread.

#### 5. What do you understand by "listener thread in detached mode"?

  - Creating a thread in detached mode means that its resources will automatically be freed upon termination, without needing another thread to join it.
  
#### 6. What's the role of the 'Receive Buffer' in the networking logic?

  - The receive buffer is allocated to temporarily store incoming packets before they are processed by the application-specific callback function.
  
#### 7. Is there any provision for thread cancellation in the existing code? 
  
  - No, the existing code does not include logic for thread cancellation. That is part of an assignment to implement.
  
#### 8. How is the main application notified of packet arrival?

  - A pre-defined callback function is invoked to notify the main application once a packet is received. This allows for custom processing of the incoming packet.

---

These notes should help you understand the intricacies of the code and prepare for interviews. Good luck! 🍀
