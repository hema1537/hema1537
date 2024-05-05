import random

class Ludo:
    def __init__(self):
        self.board = [0] * 52
        self.players = ["Red", "Green", "Blue", "Yellow"]
        self.positions = {"Red": 0, "Green": 13, "Blue": 26, "Yellow": 39}

    def move(self, player, steps):
        current_position = self.positions[player]
        new_position = (current_position + steps) % 52
        self.positions[player] = new_position

    def play(self):
        while True:
            for player in self.players:
                input(f"{player}'s turn. Press Enter to roll the dice.")
                steps = random.randint(1, 6)
                print(f"{player} rolled {steps}.")
                self.move(player, steps)
                print(f"{player} is now at position {self.positions[player]}.")
                if self.positions[player] == 51:
                    return f"{player} wins!"

if __name__ == "__main__":
    game = Ludo()
    print("Starting Ludo game...\n")
    result = game.play()
    print("\nGame Over!")
    print(result)
