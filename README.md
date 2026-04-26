# 🤖 Fine-tuning LLM for Candidate Screening

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://www.python.org/)
[![Unsloth](https://img.shields.io/badge/Unsloth-QLoRA-orange)](https://github.com/unslothai/unsloth)
[![Ollama](https://img.shields.io/badge/Ollama-Compatible-green)](https://ollama.com/)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

> 🎯 Дообучение языковой модели **Llama 3.2 3B** для автоматической оценки соответствия кандидатов вакансиям. Модель возвращает структурированный JSON-ответ с оценкой, решением и обоснованием.

---

## 📋 О проекте

Этот репозиторий содержит полный пайплайн fine-tuning для задачи HR-скрининга:

Резюме + Вакансия → Модель → {"score": 75, "match": true, "reason": "..."}


### ✨ Особенности

- 🔥 **QLoRA 4-bit обучение** через [Unsloth](https://github.com/unslothai/unsloth) — в 2-5 раз быстрее, экономит память
- 💻 **Запуск на Google Colab T4** (бесплатно, 16 ГБ VRAM)
- 📦 **Экспорт в Ollama GGUF** — запуск модели локально на CPU
- 🧩 **Интеграция с FastAPI + Chainlit** — готовое веб-приложение для скрининга
- 📊 **Автоматическая генерация датасета** из CSV с кандидатами и вакансиями
- 🎨 **Аугментация промптов** — улучшение обобщающей способности модели

---

## 🚀 Быстрый старт

### 1. Запуск обучения в Colab

1. Откройте ноутбук: [`FineTuning.ipynb`](./FineTuning.ipynb) в [Google Colab](https://colab.research.google.com/)
2. Выберите среду выполнения: **GPU (T4)**
3. Запустите ячейки по порядку:
   - Установка зависимостей
   - Загрузка модели + LoRA адаптеры
   - Генерация датасета (вставьте свои CSV)
   - Обучение (~5-45 мин в зависимости от размера датасета)
   - Экспорт в GGUF + скачивание

### 2. Импорт модели в Ollama

После скачивания архива с моделью:

```bash
# Распакуйте архив
unzip model_for_ollama.zip
cd final_model_pack

# Импортируйте модель в Ollama
ollama create screening-test:3b -f Modelfile

# Запустите
ollama run screening-test:3b
```


## 📦 Требования
### Для обучения (Colab)
* Google Colab с GPU T4 (бесплатно)
* Интернет-соединение для загрузки модели
### Для запуска модели локально
* Ollama ≥ 0.1.30
* CPU с ≥8 ГБ RAM (для Q4_K_M)
* Или GPU с ≥6 ГБ VRAM для ускорения
### Для интеграции с приложением
* Python 3.10+
* httpx или langchain-ollama
* Docker (опционально, для контейнеризации)
