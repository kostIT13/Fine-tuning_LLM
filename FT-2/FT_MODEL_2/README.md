# 🤖 Screening Test: Llama 3.2 3B (Full Dataset)

![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)
![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![Ollama](https://img.shields.io/badge/Ollama-Compatible-orange)
![Fine-tuning](https://img.shields.io/badge/Fine--tuning-QLoRA-green)

> Модель для автоматического скрининга кандидатов — **готовая для продакшена**

Модель дообучена методом **QLoRA (4-bit)** через [Unsloth](https://github.com/unslothai/unsloth) на **500 примерах** для задачи автоматической оценки соответствия резюме вакансии.

✅ **Рекомендуется для продакшена** — стабильный JSON, высокая точность, лаконичные ответы.

---

## 📥 Быстрый старт с Ollama

```bash
# 1. Импортируй модель из репозитория
ollama create screening-test:3b -f https://huggingface.co/jiikoool/screening-test3b/raw/main/Modelfile

# 2. Запусти
ollama run screening-test:3b

# 3. Пример запроса:
>>> Оцени соответствие кандидата вакансии.
>>> Резюме: Опыт разработки на Python, Django. Работа с PostgreSQL. Стаж 3 года.
>>> Вакансия: Требуется Backend Developer (Python), опыт 3-5 лет, стек Django, PostgreSQL.


## 📊 Параметры обучения

| Параметр | Значение |
|----------|----------|
| **Базовая модель** | `meta-llama/Llama-3.2-3B-Instruct` |
| **Метод** | QLoRA 4-bit (Unsloth) |
| **Ранг LoRA** | r=16, alpha=16 |
| **Шаги обучения** | 5 |
| **Эпохи** | ~3 |
| **Батч** | 8 (2×4) |
| **LR** | 1e-4 |
| **Датасет** | 500 пар "резюме-вакансия" (синтетические) |
| **GPU** | Google Colab T4 (16GB VRAM) |
| **Время обучения** | ~5 минут |
| **Max Seq Length** | 1024 |
| **Optimizer** | adamw_8bit |
| **Precision** | fp16 |


## Ссылки

* 🤗 [Репозиторий модели на Hugging Face](https://huggingface.co/jiikoool/screening-test3b/tree/main)
* 💻 [Исходный код проекта на GitHub](https://github.com/kostIT13/AI-system-for-screening-candidates)