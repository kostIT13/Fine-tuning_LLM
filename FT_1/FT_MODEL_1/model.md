---
language:
  - ru
  - en
tags:
  - gguf
  - llama-3.2
  - 3b
  - finetuning
  - unsloth
  - ollama
  - screening
  - recruitment
  - qlora
  - peft
license: apache-2.0
base_model: meta-llama/Llama-3.2-3B-Instruct
pipeline_tag: text-generation
---

# 🤖 Screening Test: Llama 3.2 3B (Fine-tuned)

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
