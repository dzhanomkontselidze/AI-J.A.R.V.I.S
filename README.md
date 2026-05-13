# J.A.R.V.I.S. — Telegram AI Бот 🤖

> *Just A Rather Very Intelligent System*

Sophisticated Telegram бот на базі **Google Gemini** та **Stability AI**, побудований за допомогою **n8n** автоматизації. JARVIS відповідає з елегантністю, сухим гумором та бездоганною компетентністю — як особистий AI асистент генія-мільярдера.

---

## ✨ Можливості

| Команда | Опис |
|---|---|
| 💬 **(без команди)** | Чат з JARVIS — відповідає на будь-яке повідомлення |
| `/start` | Привітальне повідомлення з представленням JARVIS |
| `/image [запит]` | Генерація зображення через Stability AI |
| `/test [текст]` | Створення квізу з будь-якого наданого тексту |
| `/help` | Показати доступні команди |

- 🌍 **Автоматичне визначення мови** — відповідає мовою користувача
- 😄 **Випадковий стікер** + повідомлення про помилку для непідтримуваних команд
- ⚡ **Завжди активний** — не потребує ручного запуску

---

## 🛠️ Технології

- [n8n](https://n8n.io) — Автоматизація робочих процесів
- [Google Gemini](https://ai.google.dev) — AI чат та відповіді
- [Stability AI](https://stability.ai) — Генерація зображень
- [Telegram Bot API](https://core.telegram.org/bots/api) — Платформа бота

---

## 🚀 Встановлення

### Вимоги
- n8n (хмарний або самостійно розгорнутий)
- Telegram Bot Token (від [@BotFather](https://t.me/BotFather))
- Google Gemini API ключ (з [aistudio.google.com](https://aistudio.google.com))
- Stability AI API ключ (з [platform.stability.ai](https://platform.stability.ai))

### Інструкція

1. **Встанови файл JSON**
   
3. **Імпортуй workflow в n8n**
   - Відкрий n8n
   - Натисни **Import from file**
   - Вибери JSON файл workflow

4. **Додай свої облікові дані в n8n**
   - Telegram Bot API токен
   - Google Gemini API ключ
   - Stability AI API ключ (Header Auth)

5. **Активуй workflow**
   - Натисни перемикач **Active** в n8n

---

## 📁 Структура Workflow

```
Telegram Trigger
  → PreProcessing
  → Settings
  → Merge
  → CheckCommand
      ├─ 0: Звичайний чат  → Jarvis Default (Gemini) → Відповідь
      ├─ 1: /start         → Jarvis Welcome (Gemini) → Відповідь
      ├─ 2: /image         → HTTP Request (Stability AI) → Code → Фото
      ├─ 3: /help          → Jarvis Help (Gemini) → Відповідь
      └─ CheckCommand2
            ├─ 0: /test    → Jarvis Test (Gemini) → Code → Відповідь
            └─ 1: помилка  → Jarvis Error → Code → Стікер + Текст
```

---

## 💬 Приклади використання JARVIS

```
Користувач: Привіт!
JARVIS: Доброго дня. Я вже передбачив ваше привітання
        і підготував відповідь заздалегідь. Чим можу допомогти? 🤖

Користувач: /image кіт у костюмі у стилі Гіблі
JARVIS: [генерує та надсилає зображення] 🎨

Користувач: /test Фотосинтез — це процес за допомогою якого рослини...
JARVIS: [генерує 5 питань квізу з тексту] 📝
```

---

## ⚙️ Налаштування

### Особистість JARVIS
Бот використовує спеціальний системний промпт який надає йому характер JARVIS:
- Витончений та точний
- Сухий гумор та елегантність
- Відповідає мовою користувача
- Іноді звертається до користувача на ім'я

### Підтримувані мови
Автоматично визначає та відповідає будь-якою мовою якою пише користувач.

---

## 📝 Примітки

- Gemini безкоштовний рівень: **1500 запитів/день** (використовуй `gemini-1.5-flash` або `gemini-2.0-flash`)
- Stability AI безкоштовний рівень: ~**25 зображень** при реєстрації
- n8n Cloud безкоштовний рівень додає футер "powered by n8n"

---


*Створено з ❤️ та краплею натхнення від Stark Industries*
