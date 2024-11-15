# Tour de France AI

## Introduction

This project implements a board game *Tour de France* with two AI players and two human players. The main objective of the project is to simulate the game intelligently using Artificial Intelligence (AI) techniques in Prolog. The project also includes a chatbot designed to answer users' questions about the game's rules. This document details the project’s architecture, how the AI works, the heuristics used, and the web interface implementation.

## Web Implementation of the Game

The web interface allows human players to play the game using a frontend built with HTML, CSS, and JavaScript. Every time a player (whether human or AI) moves a cyclist, a request is sent to a Prolog server, which returns the updated game board state.

### 1. Front End

The frontend consists of HTML, CSS, and JavaScript files:
- The game board is represented by an image of the actual game board.
- Cyclists are represented as colored dots corresponding to their team.
- Players interact with the interface to make their moves (selecting a cyclist, using cards, etc.).

### 2. Prolog Server

The Prolog server handles requests from the players, whether for a human player's move or an AI action. The server is composed of several files:
- `serveur.pl`: the main file that handles HTTP requests and sends the appropriate responses.
- `deplacement_manuel.pl`: handles the moves of human players.
- `deplacement_IA_2.pl` and `deplacement_IA_4.pl`: handle the moves for the respective AI players.
- `chatbot.pl`: manages the responses for the chatbot.
- `predicat_helper.pl`: contains utility predicates used by other files.

## Artificial Intelligence Functionality

### 1. The Algorithm

The AIs operate using a MinMax algorithm adapted for four players. A decision tree is generated where each node represents a possible move for a player. A score is assigned to each branch, indicating the advantage for each player. The AI chooses the moves that maximize its score.

### 2. Heuristics

Two heuristics were tested:
- **AI for Player 2**: always moves its least advanced cyclist.
- **AI for Player 4**: always uses its highest card first.

### 3. Heuristic Comparison

After testing both heuristics, it was concluded that the heuristic for Player 2 (moving the least advanced cyclist) is more efficient, as it helps the team stay grouped and better use the draft. On the other hand, Player 4’s heuristic allows one cyclist to take the lead but leaves the rest of the team lagging behind.

## ChatBot

The chatbot, developed in Prolog, answers user questions about the game rules. It works by identifying keywords in the questions and selecting the most appropriate response from a predefined list. While this rule-based system is useful, it is limited compared to more advanced AI systems capable of fully understanding and reasoning with natural language.

## Getting Started with the Interface

### 1. Prolog Server

To start the Prolog server, simply run the following commands:
```bash
swipl
[serveur].
server(8000).

npm install cors-anywhere
cd node_modules/cors-anywhere/lib
npm run start
