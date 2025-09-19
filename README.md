# 🔧 Установка Ramus на macOS

Это руководство поможет вам установить и запустить Ramus на macOS.

## 📋 Основная установка

Выполните следующие команды в Терминале по порядку:

```bash
# 1. Клонируем репозиторий
git clone https://github.com/Vitaliy-Yakovchuk/ramus.git

# 2. Переходим в папку проекта
cd ramus

# 3. Устанавливаем Homebrew (если не установлен)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 4. Добавляем Homebrew в PATH
export PATH="/opt/homebrew/bin:$PATH"

# 5. Устанавливаем OpenJDK 11
brew install openjdk@11

# 6. Добавляем Java в PATH
export PATH="/opt/homebrew/opt/openjdk@11/bin:$PATH"

# 7. Устанавливаем JAVA_HOME
export JAVA_HOME="/opt/homebrew/opt/openjdk@11/libexec/openjdk.jdk/Contents/Home"

# 8. Обновляем конфигурацию shell
source ~/.zshrc

# 9. Запускаем приложение
./gradlew runLocal
```

## 🔧 Устранение неполадок

### Проблема с зависимостью `docking-frames-common`

Если возникает ошибка `'org.dockingframes:docking-frames-common:1.1.2-SNAPSHOT'`:

1. **Откройте Finder** и перейдите в папку `ramus`
2. **Перейдите** в папку `gui-framework-core`
3. **Откройте** файл `build.gradle` в приложении TextEdit
4. **Измените** строку:
   ```gradle
   # Было:
   implementation 'org.dockingframes:docking-frames-common:1.1.2-SNAPSHOT'
   
   # Стало:
   implementation 'org.dockingframes:docking-frames-common:1.1.1'
   ```
5. **Сохраните** файл
6. **Вернитесь** в Терминал и перейдите в папку `ramus`:
   ```bash
   cd ramus
   ./gradlew runLocal
   ```

### Проблема с версией Java

Если установлена другая версия Java и она постоянно меняется:

1. **Откройте** конфигурационный файл:
   ```bash
   nano ~/.zshrc
   ```

2. **Найдите** строку:
   ```bash
   export JAVA_HOME=$(/usr/libexec/java_home -v 17)
   ```
   
3. **Измените** версию с `17` на `11`:
   ```bash
   export JAVA_HOME=$(/usr/libexec/java_home -v 11)
   ```

4. **Сохраните** изменения:
   - Нажмите `Ctrl + X`
   - Нажмите `Y`
   - Нажмите `Enter`

5. **Запустите** приложение:
   ```bash
   cd ramus
   ./gradlew runLocal
   ```

## ⚡ Быстрый старт

После первоначальной настройки для запуска Ramus достаточно:

```bash
cd ramus
./gradlew runLocal
```
