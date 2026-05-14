# Руководство по установке HackedServer

Подробное пошаговое руководство для установки и настройки HackedServer на вашем сервере.

---

## 📋 Оглавление

- [Быстрая установка](#быстрая-установка)
- [Системные требования](#системные-требования)
- [Полная установка](#полная-установка)
- [Конфигурация](#конфигурация)
- [Проверка установки](#проверка-установки)
- [Решение проблем](#решение-проблем)
- [Первый запуск](#первый-запуск)

---

## Быстрая установка

Если вы опытный пользователь, вот краткая инструкция:

```bash
# 1. Скачайте плагин
cd ~/server/plugins
wget https://github.com/Mukller/Hackedserver-/releases/download/v3.16.1/hackedserver-3.16.1.jar

# 2. Запустите сервер
cd ~/server
./start.sh

# 3. Проверьте установку
# В консоли сервера выполните:
/hs status
```

---

## Системные требования

### Минимальные требования

```
Java:          Java 8+
RAM сервера:   512 MB (плюс обычные требования)
Версия MC:     1.8.x - 1.21.x
Место на диске: 100 MB
```

### Рекомендуемые требования

```
Java:          Java 17+ (LTS)
RAM сервера:   2 GB+ для плагина
Версия MC:     1.20.x - 1.21.x
Место на диске: 500 MB
Server SW:     Paper или Purpur
```

### Проверка Java

```bash
# Проверьте версию Java
java -version

# Вывод должен быть:
# openjdk version "17.0.1" 2021-10-19
# или выше
```

---

## Полная установка

### Шаг 1: Подготовка сервера

```bash
# Перейдите в корневую папку сервера
cd /path/to/minecraft/server

# Проверьте структуру папок
ls -la
# Должны быть: plugins/, world/, logs/ и т.д.

# Убедитесь, что папка plugins существует
mkdir -p plugins
```

### Шаг 2: Скачивание плагина

**Способ 1: Через wget**
```bash
cd plugins
wget https://github.com/Mukller/Hackedserver-/releases/download/v3.16.1/hackedserver-3.16.1.jar
ls -lh hackedserver-3.16.1.jar
```

**Способ 2: Через curl**
```bash
cd plugins
curl -L -O https://github.com/Mukller/Hackedserver-/releases/download/v3.16.1/hackedserver-3.16.1.jar
```

**Способ 3: Ручное скачивание**
1. Перейдите на https://github.com/Mukller/Hackedserver-/releases
2. Скачайте `hackedserver-3.16.1.jar`
3. Переместите в папку `plugins/`

### Шаг 3: Установка прав доступа

```bash
# Linux/Mac
chmod 644 plugins/hackedserver-3.16.1.jar
chown minecraft:minecraft plugins/hackedserver-3.16.1.jar

# Проверка
ls -l plugins/hackedserver-3.16.1.jar
# Должно быть: -rw-r--r--
```

### Шаг 4: Запуск сервера

```bash
# Убедитесь, что вы находитесь в корневой папке сервера
cd /path/to/minecraft/server

# Запустите сервер
./start.sh
# или
java -Xmx2G -jar server.jar nogui
```

**Вывод в консоль должен содержать:**
```
[Loading]
[HackedServer] Loading...
[HackedServer] HackedServer 3.16.1 has been enabled!
[HackedServer] Configuration loaded successfully
[Done] Done (1.5s)!
```

### Шаг 5: Проверка логов

```bash
# Проверьте логи на ошибки
tail -50 logs/latest.log | grep HackedServer

# Вывод должен быть:
# [HackedServer] Enabling HackedServer v3.16.1
# [HackedServer] Configuration: enabled=true
# [HackedServer] Ready to detect cheaters!
```

---

## Конфигурация

### Первый запуск

После первого запуска создается файл конфигурации:

```
plugins/HackedServer/config.yml
```

### Редактирование конфигурации

```bash
# Откройте файл конфигурации
nano plugins/HackedServer/config.yml
```

### Основные параметры

```yaml
# ===== Основные настройки =====
enabled: true
debug: false

# ===== Режим детектирования =====
# STRICT - максимальная защита, много ложных срабатываний
# NORMAL - сбалансированный режим (рекомендуется)
# PERMISSIVE - мягкий режим, пропускает некоторые читы
detection-mode: NORMAL

# ===== Что проверять =====
detectors:
  aimbot: true
  speed-hack: true
  fly-hack: true
  killaura: true
  reach-hack: true
  noclip: true

# ===== Действие при обнаружении =====
# KICK - выкинуть из сервера
# BAN - забанить игрока
# WARN - предупредить администратора
punishment:
  action: KICK
  ban-duration: 7d  # 7 дней
  kick-message: "&cВы были выкинуты за использование читов!"

# ===== Логирование =====
logging:
  enabled: true
  file: plugins/HackedServer/logs/events.log
  level: INFO

# ===== Уведомления =====
notifications:
  enabled: true
  notify-admins: true
  discord-webhook: ""  # оставьте пусто если не нужен Discord

# ===== Белый список (исключения) =====
whitelist:
  enabled: false
  players: []
  # whitelist:
  #   players:
  #     - "AdminName"
  #     - "ModName"
```

### Сохранение изменений

```bash
# Сохраните файл (Ctrl + O, Enter, Ctrl + X если используете nano)

# Перезагрузите конфигурацию
# В консоли сервера:
/hs reload
```

---

## Проверка установки

### Команды для проверки

```bash
# В консоли сервера (после входа оператора на сервер):

# Проверьте статус плагина
/hs status

# Вывод должен быть:
# HackedServer 3.16.1 is running
# Status: ENABLED
# Mode: NORMAL
# Detected cheaters: 0
```

### Проверка в логах

```bash
# Проверьте логи на ошибки
grep -i "error\|exception" logs/latest.log

# Вывод должен быть пуст или содержать только старые ошибки
```

### Проверка файлов

```bash
# Проверьте структуру файлов
tree -L 2 plugins/HackedServer/

# Должно быть:
# plugins/HackedServer/
# ├── config.yml
# ├── logs/
# │   └── events.log
# └── data/
#     ├── whitelist.yml
#     └── statistics.yml
```

---

## Решение проблем

### Проблема: "Plugin fails to load"

**Симптомы:**
```
[ERROR] Could not load plugin from file plugins/hackedserver-3.16.1.jar
java.lang.ClassNotFoundException: ...
```

**Решение:**
1. Проверьте версию Java:
   ```bash
   java -version
   # Должно быть Java 8+
   ```

2. Проверьте целостность файла:
   ```bash
   ls -lh plugins/hackedserver-3.16.1.jar
   # Размер должен быть > 1 MB
   ```

3. Переустановите плагин:
   ```bash
   rm plugins/hackedserver-3.16.1.jar
   cd plugins
   wget https://github.com/Mukller/Hackedserver-/releases/download/v3.16.1/hackedserver-3.16.1.jar
   ```

### Проблема: "Configuration error"

**Симптомы:**
```
[ERROR] HackedServer] Error parsing configuration file
```

**Решение:**
1. Проверьте YAML синтаксис:
   ```yaml
   # ✅ Правильно:
   enabled: true
   mode: NORMAL
   
   # ❌ Неправильно:
   enabled:true
   mode=NORMAL
   ```

2. Используйте конвертер YAML:
   - https://www.yamllint.com/

3. Восстановите конфигурацию:
   ```bash
   rm plugins/HackedServer/config.yml
   # Перезагрузите сервер - создастся новая конфигурация
   /reload
   ```

### Проблема: "High CPU usage"

**Решение:**
1. Уменьшите количество проверок:
   ```yaml
   detectors:
     aimbot: true
     reach-hack: false     # отключите
     noclip: false         # отключите
   ```

2. Увеличьте интервал проверок:
   ```yaml
   check-interval: 500ms   # 500 миллисекунд вместо 250
   ```

3. Увеличьте RAM сервера:
   ```bash
   # Измените в start.sh:
   java -Xmx4G -jar server.jar nogui
   ```

### Проблема: "Too many false positives"

**Решение:**
1. Переключитесь на PERMISSIVE режим:
   ```yaml
   detection-mode: PERMISSIVE
   ```

2. Отключите чувствительные детекторы:
   ```yaml
   detectors:
     aimbot: false         # отключите
     killaura: false       # отключите
   ```

3. Добавьте игроков в белый список:
   ```yaml
   whitelist:
     enabled: true
     players:
       - "PlayerName1"
       - "PlayerName2"
   ```

---

## Первый запуск

### Что ожидать

**При первом включении:**
- Плагин создаст файлы конфигурации
- Создастся папка логов
- Плагин будет готов к работе в течение 5-10 секунд

**Что вы увидите в консоли:**
```
[15:30:45] [Server thread/INFO]: [HackedServer] Loading...
[15:30:45] [Server thread/INFO]: [HackedServer] Hooking into Minecraft...
[15:30:45] [Server thread/INFO]: [HackedServer] Configuration loaded!
[15:30:46] [Server thread/INFO]: [HackedServer] HackedServer 3.16.1 enabled!
```

### Первые действия

```bash
# 1. Проверьте статус плагина
/hs status

# 2. Просмотрите доступные команды
/hs help

# 3. Проверьте конфигурацию
/hs config

# 4. Посмотрите логи
/hs logs
```

### Тестирование

```bash
# 1. Присоединитесь к серверу в режиме администратора
# 2. Выполните команду:
/hs check <ваше_имя>

# 3. Вывод должен быть:
# Player: YourName | Status: CLEAN
```

---

## Следующие шаги

После установки рекомендуется:

1. **Прочитайте документацию** — [README.md](README.md)
2. **Настройте конфигурацию** — под ваши потребности
3. **Подключите Discord** — для уведомлений
4. **Обучите администраторов** — основным командам
5. **Мониторьте логи** — в течение первой недели

---

## Получение помощи

Если что-то не работает:

1. **Проверьте логи** — `tail -100 logs/latest.log`
2. **Посмотрите FAQ** — в [README.md](README.md#часто-задаваемые-вопросы)
3. **Создайте Issue** — на GitHub с подробным описанием
4. **Напишите разработчику** — [@Mukller](https://github.com/Mukller)

---

**Спасибо за использование HackedServer! 🎮**

*Последнее обновление: 14 мая 2024 г.*
