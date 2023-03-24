# Tic-Tac-Toe-Game-using-GUI-Programming-in-Python

The above code is an implementation of a Tic Tac Toe game using Python and the Tkinter GUI toolkit. The game is played on a 3x3 grid of buttons, where each player takes turns clicking on a button to mark their symbol (X or O) on the board. The first player to get three of their symbols in a row (horizontally, vertically, or diagonally) wins the game.

Here is a step-by-step breakdown of the code:
1.Import the necessary modules:
                       import tkinter as tk
                       from tkinter import messagebox
    The tkinter module provides the main GUI widgets, while messagebox is used to display message boxes.
     
2.Define the TicTacToe class:
    class TicTacToe:
    def __init__(self, master):
        self.master = master
        self.master.title("Tic Tac Toe")
        self.current_player = "X"
        self.board = [" "]*9
        self.create_widgets()

     The __init__ method initializes the game by setting the game window title, initializing the current player to "X", and creating the game board (which consists of a 3x3 grid of buttons).
     
3.Create the game board:
 def create_widgets(self):
    # create the game board
    self.board_frame = tk.Frame(self.master)
    self.board_frame.pack()
    self.buttons = []
    for i in range(9):
        button = tk.Button(self.board_frame, text="", width=6, height=3,
                           font=("Helvetica", 20), command=lambda i=i:
                           self.handle_click(i))
        button.grid(row=i // 3, column=i % 3)
        self.buttons.append(button)
        
        The create_widgets method creates the game board by creating a Frame widget to hold the buttons, then creating 9 Button widgets with empty text, a fixed width and height, a font size of 20, and a command that calls the handle_click method when the button is clicked. The buttons are then arranged in a 3x3 grid using the grid geometry manager, and the buttons are added to the self.buttons list.
        
 4.Set the background color of the X's and O's:
     # set the background color of the X's to red and the O's to blue
    self.buttons[::2] = [button.configure(bg="red") or button for button in self.buttons[::2]]
    self.buttons[1::2] = [button.configure(bg="blue") or button for button in self.buttons[1::2]]
    
This code sets the background color of the X's and O's by modifying every other button in the self.buttons list (starting with the first button) using a slice with a step of 2. We set the background color of the X's to red and the background color of the O's to blue.

5.Define the handle_click method:
    def handle_click(self, i):
        if self.board[i] == " ":
            self.board[i] = self.current_player
            self.buttons[i].configure(text=self.current_player)
            if self.check_win():
                messagebox.showinfo("Congratulations!", f"{self.current_player} wins!")
                self.reset_game()
            elif " " not in self.board:
                messagebox.showinfo("Tie Game!", "The game ended in a tie.")
                self.reset_game()
            else:
                self.current_player = "O" if self.current_player == "X
                
 The handle_click method is called when a button on the game board is clicked. It takes a single argument i, which represents the index of the button that was clicked.




 
 
  
    

      
