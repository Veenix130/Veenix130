👋 Привет, я Veenix130
<div align="center">
🚀 Junior Developer
💻 Изучаю разработку и постоянно совершенствую свои навыки 🔥 Увлекаюсь созданием приложений, автоматизацией и изучением новых технологий
</div>

⸻
 
🎯 Сейчас изучаю
Современный .NET и экосистему C#
Архитектуру приложений
Алгоритмы и структуры данных
Оптимизацию кода на C++
Автоматизацию задач с помощью Python
 
⸻
 
🌟 О себе
🔹 Junior Developer
🔹 Люблю изучать новые технологии
🔹 Открыт для интересных проектов
🔹 Постоянно развиваюсь и прокачиваю навыки

⸻
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Veenix130&layout=compact&theme=tokyonight&hide_border=true" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Veenix130&show_icons=true&theme=tokyonight&hide_border=true" />
</p>

## 🛠 Tech Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=cs,cpp,python,dotnet,visualstudio,vscode,git,github,linux" />
</p>
Контакты
📧 Email: Veenix130@yandex.ru
💬 Telegram: @veenix
🌐 GitHub: https://github.com/Veenix130
</div>
 
⸻
 
<div align="center">
⭐ Спасибо за посещение профиля!
</div>

import pygame
import random
import sys

# Инициализация
pygame.init()

# Цвета
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
RED = (213, 50, 80)
GREEN = (0, 255, 0)
BLUE = (50, 153, 213)

# Размеры окна
dis_width = 600
dis_height = 400

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption('Змейка')

clock = pygame.time.Clock()

# Параметры змейки
snake_block = 10
snake_speed = 15

# Шрифты
font_style = pygame.font.SysFont("bahnschrift", 25)
score_font = pygame.font.SysFont("comicsansms", 35)

def your_score(score):
    value = score_font.render("Счёт: " + str(score), True, BLUE)
    dis.blit(value, [0, 0])

def our_snake(snake_block, snake_list):
    for x in snake_list:
        pygame.draw.rect(dis, GREEN, [x[0], x[1], snake_block, snake_block])

def message(msg, color):
    mesg = font_style.render(msg, True, color)
    # Центрирование текста
    text_rect = mesg.get_rect(center=(dis_width/2, dis_height/2))
    dis.blit(mesg, text_rect)

def game_loop():
    game_over = False
    game_close = False

    x1 = dis_width / 2
    y1 = dis_height / 2

    x1_change = 0
    y1_change = 0

    snake_list = []
    length_of_snake = 1

    foodx = round(random.randrange(0, dis_width - snake_block) / 10.0) * 10.0
    foody = round(random.randrange(0, dis_height - snake_block) / 10.0) * 10.0

    while not game_over:

        while game_close == True:
            dis.fill(BLACK)
            message("Ты проиграл! Q-выход, C-заново", RED)
            your_score(length_of_snake - 1)
            pygame.display.update()

            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_c:
                        game_loop()

        # Управление
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT and x1_change == 0:
                    x1_change = -snake_block
                    y1_change = 0
                elif event.key == pygame.K_RIGHT and x1_change == 0:
                    x1_change = snake_block
                    y1_change = 0
                elif event.key == pygame.K_UP and y1_change == 0:
                    y1_change = -snake_block
                    x1_change = 0
                elif event.key == pygame.K_DOWN and y1_change == 0:
                    y1_change = snake_block
                    x1_change = 0

        if x1 >= dis_width or x1 < 0 or y1 >= dis_height or y1 < 0:
            game_close = True

        x1 += x1_change
        y1 += y1_change
        dis.fill(BLACK)

        # Рисуем еду
        pygame.draw.rect(dis, RED, [foodx, foody, snake_block, snake_block])

        # Логика змейки
        snake_head = []
        snake_head.append(x1)
        snake_head.append(y1)
        snake_list.append(snake_head)
        if len(snake_list) > length_of_snake:
            del snake_list[0]

        for x in snake_list[:-1]:
            if x == snake_head:
                game_close = True

        our_snake(snake_block, snake_list)
        your_score(length_of_snake - 1)

        pygame.display.update()

        # Еда
        if x1 == foodx and y1 == foody:
            foodx = round(random.randrange(0, dis_width - snake_block) / 10.0) * 10.0
            foody = round(random.randrange(0, dis_height - snake_block) / 10.0) * 10.0
            length_of_snake += 1

        clock.tick(snake_speed)

    pygame.quit()
    sys.exit()

if __name__ == "__main__":
    game_loop()
