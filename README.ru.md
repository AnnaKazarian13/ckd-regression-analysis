# Регрессионный анализ CKD / GFR

**Язык:** [English](README.md) | [Русский](#русский)

---

## Русский

### Описание
ML-проект: предсказать **GFR** (функция почек) по табличным клиническим признакам.

### Важное методологическое исправление
В финальной модели **`CKD_Status` не используется**.  
Статус ХБП обычно определяется по стадиям GFR, поэтому предсказывать GFR с помощью CKD — почти круговая зависимость / утечка.

Высокий R² всё равно ожидаем: **GFR сильно связан с Creatinine** (корреляция ≈ -0.96).

### Результаты (test, без `CKD_Status`)

| Модель | Test R² | MAE | RMSE | CV R² |
|--------|---------|-----|------|-------|
| Gradient Boosting | **0.9983** | 0.818 | 1.336 | 0.9978 |
| Linear Regression | 0.9909 | 1.754 | 3.095 | 0.9899 |

Проверка утечки (Linear Regression **с** `CKD_Status`, не финальная модель): R² ≈ 0.9931

### Запуск
```bash
pip install -r requirements.txt
jupyter notebook notebooks/ckd_regression_analysis.ipynb
```

### Автор
[AnnaKazarian13](https://github.com/AnnaKazarian13)
