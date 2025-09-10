# Git Pre-Commit Hook with Gitleaks

Цей репозиторій містить приклад **pre-commit hook** для Git, який перевіряє код на наявність секретів за допомогою [Gitleaks](https://github.com/gitleaks/gitleaks).

## 🚀 Встановлення

### 1. Скопіювати hook
cp pre-commit .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit

2. Увімкнути hook
git config gitleaks.enable true
3. 🛠️ Установка Gitleaks
  Варіант A: Через пакетний менеджер (Ubuntu/Debian)
  sudo apt update
  sudo apt install gitleaks -y
  Варіант B: Через скрипт установки
  ./scripts/install_gitleaks.sh
  Варіант C: Через GitHub Releases (останній реліз)
  GITLEAKS_VERSION=$(curl -s https://api.github.com/repos/gitleaks/gitleaks/releases/latest \
  | grep '"tag_name":' | sed -E 's/.*"v([^"]+)".*/\1/')
  wget -qO gitleaks.tar.gz "https://github.com/gitleaks/gitleaks/releases/latest/download/gitleaks_${GITLEAKS_VERSION}_linux_x64.tar.gz"
  sudo tar -xzf gitleaks.tar.gz -C /usr/local/bin gitleaks
  rm gitleaks.tar.gz
  gitleaks version
4. 🧪 Перевірка роботи
Додайте тестовий файл з секретом, наприклад TOKEN_test:
token = "123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11"
Додайте файл у staging:
git add TOKEN_test
Спробуйте закомітити:
git commit -m "Test gitleaks hook"
Якщо токен знайдено, коміт буде відхилено із повідомленням:
[gitleaks] ❌ Secrets detected! Commit aborted.