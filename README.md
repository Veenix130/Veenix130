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
<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Flowseal/Flowseal/refs/heads/output/github-contribution-grid-snake-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Flowseal/Flowseal/refs/heads/output/github-contribution-grid-snake.svg" />
    <img alt="github-snake" src="https://raw.githubusercontent.com/Flowseal/Flowseal/refs/heads/output/github-contribution-grid-snake.svg" />
  </picture>
</p>


name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

permissions:
  contents: write

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: Platane/snk@v3
        with:
          github_user_name: Veenix130
          outputs: dist/github-contribution-grid-snake.svg

      - name: Push snake
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
