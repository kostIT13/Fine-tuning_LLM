# 🤖 Screening Test: Llama 3.2 3B

![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)
![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![Ollama](https://img.shields.io/badge/Ollama-Compatible-orange)

> Модель для автоматического скрининга кандидатов

> ⚠️ **Demo-версия**: Модель дообучена на **9 примерах** для демонстрации пайплайна fine-tuning. Не рекомендуется для продакшена.

Модель дообучена методом **QLoRA (4-bit)** через [Unsloth](https://github.com/unslothai/unsloth) для задачи автоматического скрининга кандидатов: оценка соответствия резюме вакансии.

## 📥 Быстрый старт с Ollama

```bash
# 1. Импортируй модель из репозитория
ollama create screening-test:3b -f https://huggingface.co/jiikoool/screening-test/raw/main/Modelfile

# 2. Запусти
ollama run screening-test:3b

# 3. Пример запроса:
>>> Оцени соответствие кандидата вакансии.
>>> Резюме: Опыт разработки на Python, Django. Работа с PostgreSQL. Стаж 3 года.
>>> Вакансия: Требуется Backend Developer (Python), опыт 3-5 лет, стек Django, PostgreSQL.
```
### 4. Ожидаемый ответ:
```bash
{"score": 75, "match": true, "reason": "Соответствует требованиям по навыкам. Стаж подходит."}
```

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
| **Датасет** | 9 пар "резюме-вакансия" (синтетические) |
| **GPU** | Google Colab T4 (16GB VRAM) |
| **Время обучения** | ~5 минут |
| **Max Seq Length** | 1024 |
| **Optimizer** | adamw_8bit |
| **Precision** | fp16 |

---

## 📁 Файлы репозитория

| Файл | Описание |
|------|----------|
| `llama-3.2-3b-instruct.Q4_K_M.gguf` | Модель в формате GGUF (~2.2 ГБ) |
| `Modelfile` | Конфигурация для импорта в Ollama |
| `FineTuning.ipynb` | Ноутбук с полным пайплайном обучения |
| `README.md` | Этот файл |

---

## 📥 Быстрый старт с Ollama

```bash
# 1. Импортируй модель из репозитория
ollama create screening-test:3b -f https://huggingface.co/jiikoool/screening-test/raw/main/Modelfile

# 2. Запусти
ollama run screening-test:3b

# 3. Пример запроса:
>>> Оцени соответствие кандидата вакансии.
>>> Резюме: Опыт разработки на Python, Django. Работа с PostgreSQL. Стаж 3 года.
>>> Вакансия: Требуется Backend Developer (Python), опыт 3-5 лет, стек Django, PostgreSQL.
одный код проекта на GitHub
```

## Ссылки

* 🤗 [Репозиторий модели на Hugging Face](https://huggingface.co/jiikoool/screening-test/tree/main)
* 💻 [Исходный код проекта на GitHub](https://github.com/kostIT13/AI-system-for-screening-candidates)
