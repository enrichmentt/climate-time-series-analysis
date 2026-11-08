# Climate Time Series Analysis

Учебный проект по анализу и прогнозированию среднемесячной температуры в Нидерландах на данных **Climate Change: Earth Surface Temperature Data**.

## Что сделано

- подготовлен месячный временной ряд с индексом-датой;
- выполнено хронологическое holdout-разбиение 80/20;
- реализовано rolling-window-разбиение: окно обучения — 120 месяцев, горизонт прогноза — 12 месяцев;
- созданы лаги на 1 и 12 месяцев, номер месяца и индикатор зимнего сезона;
- обучена линейная регрессия и построен прогноз на тестовой выборке;
- рассчитаны MAE, RMSE и MAPE.

Все ячейки ноутбука выполнены: в файле сохранены графики, таблицы и результаты расчётов.

## Результаты

| Метрика | Значение |
|---|---:|
| MAE | 1,484 °C |
| RMSE | 1,929 °C |
| MAPE | 51,472% |

MAPE менее устойчива для температур в шкале Цельсия из-за значений, близких к нулю, поэтому при интерпретации качества полезно дополнительно ориентироваться на MAE и RMSE.

## Структура проекта

```text
climate-time-series-analysis/
├── climate-time-series-analysis.ipynb
├── data/
│   └── GlobalLandTemperaturesByCountry.csv
├── requirements.txt
├── .gitignore
└── README.md
```

## Запуск в виртуальном окружении

Рекомендуется Python 3.12.

Создайте виртуальное окружение в корне проекта:

```bash
python -m venv .venv
```

Активируйте его в Windows:

```bash
.venv\Scripts\activate
```

Или в macOS / Linux:

```bash
source .venv/bin/activate
```

Установите зависимости и откройте ноутбук:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter notebook climate-time-series-analysis.ipynb
```

Датасет уже находится в каталоге `data`, поэтому отдельная загрузка и авторизация на Kaggle не требуются. Ноутбук нужно запускать из корня проекта, чтобы относительный путь к данным работал корректно.

## Данные

Используется файл `GlobalLandTemperaturesByCountry.csv` из набора [Climate Change: Earth Surface Temperature Data](https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data). Для анализа выбран непрерывный период наблюдений по Нидерландам с октября 1752 по август 2013 года.
