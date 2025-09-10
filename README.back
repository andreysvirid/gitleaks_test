# Git Pre-Commit Hook with Gitleaks

Цей репозиторій містить приклад pre-commit hook для `git`, який перевіряє код на наявність секретів за допомогою [gitleaks](https://github.com/gitleaks/gitleaks).

## 🚀 Встановлення

1. Клонувати репозиторій.
2. Файл хука `.git/hooks/pre-commit`:
   cp pre-commit .git/hooks/pre-commit
   chmod +x .git/hooks/pre-commit
3. Встановити gitleaks
   chmod +x ./install_gitleaks.sh
   ./install_gitleaks.sh
   gitleaks version
4. Увімкнути хук
   git config gitleaks.enable true
5. Тестування
   Додати у файл тестовий токен
   token = "123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11"
   cat TOKEN_test
   git add .
   git commit -m "test gitleaks"
   Коміт повинен бути відхилений з повідомленням:
   [gitleaks] ❌ Secrets detected! Commit aborted.