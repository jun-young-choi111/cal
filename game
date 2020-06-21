import pygame
import slid
import math
from player import Player
from game_state import GameState


class Game:
    def __init__(self, screen):
        self.screen = screen
        self.objects = []
        self.game_state = GameState.none
        self.map = []
        

    def set_up(self):
        player = Player(1, 1)
        self.player = player
        self.objects.append(player)
        self.game_state = GameState.playing
        self.load_map("02")

    def update(self):
        self.screen.fill(slid.BLACK)
        self.handle_events()
        self.render_map(self.screen)
        for object in self.objects:
            object.make(self.screen)

       

    def handle_events(self):
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                self.game_state = GameState.end
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_ESCAPE:
                    self.game_state = GameState.ENDED
                elif event.key == pygame.K_w:  
                    self.player.update_position(0, -1)
                elif event.key == pygame.K_s:  
                    self.player.update_position(0, 1)
                elif event.key == pygame.K_a:  
                    self.player.update_position(-1, 0)
                elif event.key == pygame.K_d:  
                    self.player.update_position(1, 0)

    def load_map(self, file_name):
        with open('maps/' + file_name + ".txt") as map_file:
            for line in map_file:
                tiles = []
                for i in range(0, len(line) - 1, 2):
                    tiles.append(line[i])
                self.map.append(tiles)
            print(self.map)

    def render_map(self, screen):
        y_pos = 0
        for line in self.map:
            x_pos = 0
            for tile in line:
                image = map_background_image[tile]
                rect = pygame.Rect(x_pos * slid.size, y_pos * slid.size, slid.size, slid.size)
                screen.blit(image, rect)
                x_pos = x_pos + 1

            y_pos = y_pos + 1
   
map_background_image = {
        "T": pygame.transform.scale(pygame.image.load("imgs/tree.png"), (slid.size, slid.size)),
        "F": pygame.transform.scale(pygame.image.load("imgs/grass.png"), (slid.size, slid.size)),
        "Q": pygame.transform.scale(pygame.image.load("imgs/water1.png"), (slid.size, slid.size)),
        "R": pygame.transform.scale(pygame.image.load("imgs/water2.png"), (slid.size, slid.size)),
        "U": pygame.transform.scale(pygame.image.load("imgs/water3.png"), (slid.size, slid.size)),
        "Y": pygame.transform.scale(pygame.image.load("imgs/water4.png"), (slid.size, slid.size)),
        "G": pygame.transform.scale(pygame.image.load("imgs/ground.png"), (slid.size, slid.size)),
        "H": pygame.transform.scale(pygame.image.load("imgs/house.png"), (slid.size, slid.size)),
        "C": pygame.transform.scale(pygame.image.load("imgs/center.png"), (slid.size, slid.size))
    }
