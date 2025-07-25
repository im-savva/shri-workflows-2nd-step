# Инструкции по работе с багами и правками

> ШРИ, 2025, 2 этап

## 1. Как реагировать на баги

### 1.1 Первичная реакция
- **Не паникуйте:** Баги — это часть разработки, главное их правильно обработать
- **Воспроизведите баг:** Убедитесь, что можете стабильно воспроизвести проблему
- **Оцените масштаб:** Понимание затрагивает ли баг критичный функционал

### 1.2 Фиксация бага
- **Фиксируйте баг немедленно:** При обнаружении бага сразу фиксируйте его в системе трекинга (GitHub Issues, Jira, Trello и т.д.)
- **Используйте шаблон описания:**
  ```markdown
  ## Описание бага
  Краткое описание проблемы
  
  ## Шаги для воспроизведения
  1. Шаг 1
  2. Шаг 2
  3. Шаг 3
  
  ## Ожидаемый результат
  Что должно было произойти
  
  ## Фактический результат
  Что произошло на самом деле
  
  ## Окружение
  - Браузер: Chrome 120.0.0.0
  - ОС: Windows 11
  - Версия приложения: v1.2.3
  - URL: https://example.com/page
  
  ## Дополнительная информация
  - Скриншоты
  - Логи консоли
  - Network requests
  ```

### 1.3 Приоритизация
- **Критичный (P0):** Полностью блокирует работу пользователей или важный бизнес-процесс
- **Высокий (P1):** Значительно влияет на пользовательский опыт, но есть workaround
- **Средний (P2):** Заметная проблема, но не критичная для основного функционала
- **Низкий (P3):** Косметические проблемы, улучшения UX

### 1.4 Назначение ответственности
- **Для критичных багов:** Немедленно уведомить тимлида/ответственного
- **Автоматическое назначение:** По компонентам (frontend/backend/devops)
- **Эскалация:** Если баг не взят в работу в течение SLA времени

## 2. Как трекать баги

- **Используйте систему трекинга:** Все баги должны быть заведены в единой системе.
- **Обновляйте статус:** Меняйте статус бага по мере продвижения (например: Open → In Progress → Resolved → Closed).
- **Добавляйте комментарии:** Фиксируйте важные детали, обсуждения и решения прямо в карточке бага.
- **Ставьте метки:** Используйте теги для фильтрации (например, `frontend`, `backend`, `UI`, `critical`).

## 3. Как исправлять баги

- **Создайте отдельную ветку:** Для каждого бага создавайте отдельную ветку в репозитории (например, `bugfix/issue-123`).
- **Пишите понятные коммиты:** В сообщении коммита указывайте номер бага и краткое описание исправления.
- **Покрывайте тестами:** По возможности добавляйте тесты, чтобы убедиться, что баг не повторится.
- **Создайте Pull Request:** После исправления создайте Pull Request и запросите ревью.
- **Проводите ревью:** Исправление должно быть проверено другим участником команды.
- **Закрывайте баг:** После мержа Pull Request и проверки на проде/стенде закройте баг в системе трекинга.

## 4. Общие рекомендации

- Не игнорируйте баги, даже если они кажутся незначительными.
- Документируйте все найденные и исправленные баги.
- Поддерживайте прозрачность и коммуникацию в команде.
- Регулярно проводите ретроспективы по багам для улучшения процессов.
