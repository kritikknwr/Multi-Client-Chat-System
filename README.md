# Multi-Client-Chat-System
Technical documentation and architecture for a Python-based multi-client chat system featuring real-time messaging and game integration
Project Overview

This project involves building a robust chat server in Python that supports multiple concurrent client connections. It facilitates real-time messaging using TCP/IP sockets and incorporates interactive elements such as a word-jumbling game and a "fun fact" generator.
Key Features

    Multi-Client Chat: Allows multiple users to connect, assign unique nicknames, and communicate in real-time.

    Word Jumble Game: Users can trigger a game using the /game command, where the server provides a shuffled word for the user to guess .

    Fun Fact Bot: Responds to the /fact command with random trivia from a pre-stored list .

    High Concurrency: Utilizes Python's threading module to manage multiple client threads simultaneously without blocking communication.

System Architecture

The system follows a classic Client-Server Architecture:

    Server Side: Listens for incoming connections, spawns a new thread for every client, and handles message broadcasting .

    Client Side: Connects via specific IP and port, sends/receives messages, and interacts with server commands .
    Shutterstock
    Explore 

Implementation Details

The project is built entirely using Python's standard libraries:

    socket: For reliable TCP/IP network communication.

    threading: To handle concurrent client interactions.

    random: For shuffling game words and selecting trivia.

Core Logic Snippets

Broadcasting Messages:
Python

def sendmessage(message, sender):
    for client in clients:
        if client != sender:
            try:
                client.send(message.encode())
            except:
                clients.remove(client) # Handles graceful disconnection [cite: 100-107]

Word Jumble Logic:
Python

def jumble():
    original = random.choice(words)
    lst = list(original)
    random.shuffle(lst)
    jumbled = "".join(lst)
    return original, jumbled [cite: 91-96]

Setup and Testing

    Connection: The server binds to a host IP and listens for connections.

    Concurrency Test: Verified that multiple clients can exchange messages and play games independently at the same time .

    Error Handling: Implemented exception handling to manage client disconnections without crashing the server .

Documentation

The full technical report, including detailed workflow analysis and testing results, is available in the repository as pythonproject_merged (1)_removed.pdf
