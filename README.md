# NLP Portfolio

Коллекция из десяти учебных проектов по обработке естественного языка и рекомендательным системам. Ноутбуки переработаны в формат портфолио: у каждого проекта есть постановка задачи, воспроизводимый эксперимент, корректные метрики, интерпретация и ограничения.

## Состав портфолио

| № | Файл | Задача | Основные навыки |
|---:|---|---|---|
| 1 | `01_russian_paraphrase_evaluation.ipynb` | Русскоязычное перефразирование | seq2seq, semantic similarity, BLEU, ROUGE |
| 2 | `02_french_english_translation_metrics.ipynb` | Перевод FR → EN | MarianMT, batched inference, SacreBLEU, TER, chrF++, BERTScore |
| 3 | `03_russian_spellchecker_noisy_channel.ipynb` | Коррекция опечаток | noisy channel, edit distance, n-граммная языковая модель, WER/CER |
| 4 | `04_hybrid_music_recommender_yambda.ipynb` | Рекомендации музыки | sparse matrices, collaborative filtering, content embeddings, rank fusion |
| 5 | `05_russian_text_detoxification.ipynb` | Детоксификация русского текста | Transformers, toxicity scoring, semantic similarity |
| 6 | `06_bengali_fake_review_detection.ipynb` | Поддельные отзывы на бенгальском | imbalanced classification, TF-IDF, Logistic Regression, Naive Bayes |
| 7 | `07_multilingual_hate_speech_explainability.ipynb` | Мультиязычная токсичность | XLM-R, model evaluation, occlusion explainability |
| 8 | `08_phishing_email_detection.ipynb` | Выявление фишинговых писем | leakage prevention, TF-IDF, PR-AUC, MCC, thresholding |
| 9 | `09_stylometric_authorship_attribution.ipynb` | Идентификация автора | character n-grams, Linear SVM, robustness testing, interpretability |
| 10 | `10_pii_masking_and_synthetic_replacement.ipynb` | Маскирование PII | T5 fine-tuning, entity-tag metrics, synthetic data |

## Запуск

Рекомендуется Python 3.11 и отдельное виртуальное окружение.

```bash
python -m venv .venv
# Windows PowerShell
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
jupyter lab
```

Большие модели и датасеты загружаются при первом запуске. Проекты 1, 5, 7 и 10 желательно выполнять на GPU. Параметры `SAMPLE_SIZE`, `MAX_ROWS`, `TRAIN_SIZE` и число эпох вынесены в начало соответствующих ноутбуков, чтобы можно было быстро запустить уменьшенный эксперимент.

## Что было исправлено

- удалены старые outputs, сообщения об ошибках и случайные демонстрационные ячейки;
- добавлены заголовки, постановка задачи, методика эксперимента и ограничения;
- устранено обучение TF-IDF и балансировка до train/test split;
- удалена метрика AER, которую невозможно корректно вычислить без word alignment;
- исправлена прямая утечка метки из текста фишинговых писем;
- исправлено несогласованное разбиение данных в проекте по стилометрии;
- оценка multilingual toxicity ограничена языками, заявленными в model card;
- проект по PII сфокусирован на маскировании и синтетической замене, без несвязанного этапа перефразирования;
- добавлены воспроизводимые random seeds и проверки схем входных данных.

## Перед публикацией

Ноутбуки сохранены без результатов выполнения. Это намеренно: опубликованные метрики должны быть получены в одном чистом окружении, а не перенесены из старых запусков с ошибками или утечками данных. Перед загрузкой на GitHub рекомендуется выполнить выбранные 3–4 проекта сверху вниз, проверить результаты и сохранить только компактные таблицы и графики.

В первую очередь для резюме подходят проекты 4, 7, 8 и 10: они показывают работу с рекомендательными системами, трансформерами, интерпретируемостью, информационной безопасностью и приватностью.
