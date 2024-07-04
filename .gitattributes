import tkinter as tk
from tkinter import messagebox
import random

class TicTacToe:
    def __init__(self):
        self.window = tk.Tk()
        self.window.title("Tic-Tac-Toe")
        self.board = [[' ' for _ in range(3)] for _ in range(3)]
        self.current_player = 'X'
        self.buttons = [[None for _ in range(3)] for _ in range(3)]
        self.create_widgets()
    
    def create_widgets(self):
        for row in range(3):
            for col in range(3):
                button = tk.Button(self.window, text=' ', font='normal 20 bold', height=2, width=4,
                                   command=lambda row=row, col=col: self.on_button_click(row, col))
                button.grid(row=row, column=col)
                self.buttons[row][col] = button
        self.reset_button = tk.Button(self.window, text='Reset', font='normal 20 bold', height=2, width=10, command=self.reset_board)
        self.reset_button.grid(row=3, column=0, columnspan=3)
    
    def on_button_click(self, row, col):
        if self.board[row][col] == ' ':
            self.board[row][col] = self.current_player
            self.buttons[row][col].config(text=self.current_player)
            if self.check_winner(self.current_player):
                messagebox.showinfo("Tic-Tac-Toe", f"Congratulations! Player {self.current_player} wins!")
                self.reset_board()
            elif self.check_draw():
                messagebox.showinfo("Tic-Tac-Toe", "It's a draw!")
                self.reset_board()
            else:
                self.current_player = 'O' if self.current_player == 'X' else 'X'
                if self.current_player == 'O':
                    self.ai_move()

    def ai_move(self):
        for row in range(3):
            for col in range(3):
                if self.board[row][col] == ' ':
                    self.board[row][col] = 'O'
                    if self.check_winner('O'):
                        self.buttons[row][col].config(text='O')
                        messagebox.showinfo("Tic-Tac-Toe", "AI wins! Better luck next time.")
                        self.reset_board()
                        return
                    self.board[row][col] = ' '
        
        for row in range(3):
            for col in range(3):
                if self.board[row][col] == ' ':
                    self.board[row][col] = 'X'
                    if self.check_winner('X'):
                        self.board[row][col] = 'O'
                        self.buttons[row][col].config(text='O')
                        self.current_player = 'X'
                        return
                    self.board[row][col] = ' '
        
        empty_spots = [(row, col) for row in range(3) for col in range(3) if self.board[row][col] == ' ']
        row, col = random.choice(empty_spots)
        self.board[row][col] = 'O'
        self.buttons[row][col].config(text='O')
        if self.check_winner('O'):
            messagebox.showinfo("Tic-Tac-Toe", "AI wins! Better luck next time.")
            self.reset_board()
        elif self.check_draw():
            messagebox.showinfo("Tic-Tac-Toe", "It's a draw!")
            self.reset_board()
        else:
            self.current_player = 'X'

    def check_winner(self, player):
        for row in self.board:
            if all([cell == player for cell in row]):
                return True
        for col in range(3):
            if all([self.board[row][col] == player for row in range(3)]):
                return True
        if all([self.board[i][i] == player for i in range(3)]) or all([self.board[i][2 - i] == player for i in range(3)]):
            return True
        return False
    
    def check_draw(self):
        return all([cell in ['X', 'O'] for row in self.board for cell in row])
    
    def reset_board(self):
        self.board = [[' ' for _ in range(3)] for _ in range(3)]
        for row in range(3):
            for col in range(3):
                self.buttons[row][col].config(text=' ')
        self.current_player = 'X'
    
    def run(self):
        self.window.mainloop()

if __name__ == "__main__":
    game = TicTacToe()
    game.run()
