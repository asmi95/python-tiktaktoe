# python-tiktaktoe
Class 12th project
<br>
while(True):
 print('1. Play the Game Tik Tak Toe')
 print('2. Graph')
 print('3. Display entire Data')
 print('4. Exit')
 ch=int(input('Enter your choice'))
 if(ch==1):
   a = input("Enter 1st person name: ")
   b = input("Enter 2nd person name: ")
   print("Hello",a,"and",b)
   print("Welcome to TICTACTOE".center(20))
   import pygame as pg
   import sys
   from random import randint
   
   WIN_SIZE = 300
   CELL_SIZE = WIN_SIZE // 3
   INF = float('inf')

   vec2 = pg.math.Vector2
   CELL_CENTER = vec2(CELL_SIZE / 2)
   class TicTacToe:
     def __init__(self, game):
       self.game = game
       self.field_image = 
self.get_scaled_image(path='C:\\Users\\User\\OneDrive\\Desktop\\Ip project\\field.png', res=[WIN_SIZE] * 2)
self.O_image = self.get_scaled_image(path='C:\\Users\\User\\OneDrive\\Desktop\\Ip project\\o.png', res=[CELL_SIZE] * 2)
self.X_image = self.get_scaled_image(path='C:\\Users\\User\\OneDrive\\Desktop\\Ip project\\x.png', res=[CELL_SIZE] * 2)
self.game_array = [[INF, INF, INF],
                   [INF, INF, INF],
                   [INF, INF, INF]]
self.player = randint(0, 1)
self.line_indices_array = [[(0, 0), (0, 1), (0, 2)],
                            [(1, 0), (1, 1), (1, 2)],
                            [(2, 0), (2, 1), (2, 2)],
                            [(0, 0), (1, 0), (2, 0)],
                            [(0, 1), (1, 1), (2, 1)],
                            [(0, 2), (1, 2), (2, 2)],
                            [(0, 0), (1, 1), (2, 2)],
                            [(0, 2), (1, 1), (2, 0)]]
self.winner = None
self.game_steps = 0
self.font = pg.font.SysFont('Verdana', CELL_SIZE // 4, True)
def check_winner(self):
 for line_indices in self.line_indices_array:
 sum_line = sum([self.game_array[i][j] for i, j in line_indices])
 
 if sum_line in {0, 3}:
 self.winner = 'XO'[sum_line == 0]
 self.winner_line = [vec2(line_indices[0][::-1]) * CELL_SIZE + CELL_CENTER,
 vec2(line_indices[2][::-1]) * CELL_SIZE + CELL_CENTER]
 
 def run_game_process(self):
 current_cell = vec2(pg.mouse.get_pos()) // CELL_SIZEcol, row = map(int, current_cell)left_click = pg.mouse.get_pressed()[0]

 if left_click and self.game_array[row][col] == INF and not 

self.winner:
 self.game_array[row][col] = self.player
 self.player = not self.player
 self.game_steps += 1
 self.check_winner()
 def draw_objects(self):
 for y, row in enumerate(self.game_array):
 for x, obj in enumerate(row):
 
 if obj != INF:
 self.game.screen.blit(self.X_image if obj else self.O_image, vec2(x, y) * CELL_SIZE)
 def draw_winner(self):
 
 if self.winner:
 pg.draw.line(self.game.screen, 'red', *self.winner_line, CELL_SIZE // 8)label = self.font.render(f'Player "{self.winner}" wins!', True, 'white', 'black')
 self.game.screen.blit(label, (WIN_SIZE // 2 - label.get_width() // 2, WIN_SIZE // 4))

 def draw(self):
 self.game.screen.blit(self.field_image, (0, 0))
 self.draw_objects()
 self.draw_winner()
 
 def get_scaled_image(path, res):
 img = pg.image.load(path)
 return pg.transform.smoothscale(img, res)
 def print_caption(self):
 pg.display.set_caption(f'Player "{"OX"[self.player]}" turn!')
 
 if self.winner:
 pg.display.set_caption(f'Player "{self.winner}" wins! Press Space to Restart')
 elif self.game_steps == 9:
 pg.display.set_caption(f'Game Over! Press Space to Restart')
 def run(self):
 self.print_caption()
 self.draw()
 self.run_game_process()
 class Game:
 def __init__(self):
 pg.init()
 self.screen = pg.display.set_mode([WIN_SIZE] * 2)
 self.clock = pg.time.Clock()
 self.tic_tac_toe = TicTacToe(self)
 def new_game(self):
 self.tic_tac_toe = TicTacToe(self)
 
 def check_events(self):
 for event in pg.event.get():
 if event.type == pg.QUIT:
 pg.quit()
 sys.exit()
 if event.type == pg.KEYDOWN:
 if event.key == pg.K_SPACE:
 self.new_game(
 def run(self):
 while True:
 self.tic_tac_toe.run()
 self.check_events()
 pg.display.update()
 self.clock.tick(60)
 if __name__ == '__main__':
 game = Game()
 game.run()
 
 elif(ch==2):
 import pymysql
 import matplotlib.pyplot as plt
 
conn=pymysql.connect(host='localhost',user='root',password='123',database='Game')
 a=conn.cursor()
 a.execute('select * from tiktaktoe')
 data=a.fetchall()
 L1=[Asmita, Sriya]
 L2=[4,3]
 plt.bar(L1,L2)
 plt.yticks([1,2,3,4,5,6])
 plt.xticks(L1)
 plt.xlabel('Players Name')
 plt.ylabel('Score')
 plt.show()
 
 conn.commit()
 elif(ch==3):
 import pymysql
 conn=pymysql.connect(host='localhost',user='root',password='123',database='Game')
 a=conn.cursor()
 a.execute('select * from tiktaktoe')
 data=a.fetchall()
 for i in data:
 for j in i:
 print(j,end=' ')
 print()
 conn.commit()
 
 elif(ch==4):
 break
 else:
 print('Invalid choice...plz enter valid choice')

