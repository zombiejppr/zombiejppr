import random

class Goku:
    def __init__(self, name, power_level):
        self.name = name
        self.power_level = power_level

    def attack(self):
        return random.randint(1, self.power_level)

class Enemy:
    def __init__(self, name, power_level):
        self.name = name
        self.power_level = power_level

    def attack(self):
        return random.randint(1, self.power_level)

def battle(player, enemy):
    print(f"A wild {enemy.name} appears!")
    while player.power_level > 0 and enemy.power_level > 0:
        player_attack = player.attack()
        enemy_attack = enemy.attack()
        print(f"{player.name} attacks {enemy.name} for {player_attack} damage.")
        enemy.power_level -= player_attack
        if enemy.power_level <= 0:
            print(f"{enemy.name} fainted. {player.name} wins!")
            break
        print(f"{enemy.name} attacks {player.name} for {enemy_attack} damage.")
        player.power_level -= enemy_attack
        if player.power_level <= 0:
            print(f"{player.name} fainted. {enemy.name} wins!")
            break

if __name__ == "__main__":
    goku = Goku("Goku", 100)
    enemy = Enemy("Frieza", 80)
    battle(goku, enemy)

