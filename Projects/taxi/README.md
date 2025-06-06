# Проект: Прогнозирование заказов такси для компании «Чётенькое такси»

## Описание проекта

Компания **«Чётенькое такси»** собирает данные о заказах такси в аэропортах для прогнозирования количества заказов на ближайший час. Это поможет:
- Привлекать больше водителей в периоды пиковых нагрузок.
- Снижать потери от неудовлетворённого спроса.

### Цель проекта:
Построить модель прогнозирования с метрикой **RMSE ≤ 48** на тестовой выборке.

## Содержание

1. Загрузка данных и подготовка  
2. Анализ  
   2.1 Вывод  
3. Создание новых признаков  
4. Обучение  
   4.1 Создание пайплайна  
   4.2 Обучение моделей  
   4.3 Обучение модели LightGBM  
   4.4 Обучение модели CatBoost  
   4.5 Подбор гиперпараметров для небустинговых моделей  
5. Тестирование  
   5.1 Анализ остатков  
6. Вывод

## Основные этапы проекта

### 1. Загрузка и подготовка данных
- Импорт данных из файла `/datasets/taxi.csv`.
- Преобразование формата данных.
- Ресемплирование по 1 часу.

### 2. Анализ данных
- Изучение распределения количества заказов.
- Выявление трендов, сезонности и аномалий.

### 3. Создание признаков
- Добавление временных признаков: день недели, час, месяц.
- Создание лаговых признаков и скользящих средних.

### 4. Обучение и подбор моделей
- Обучение разных моделей: линейные модели, RandomForest, LightGBM, CatBoost.
- Подбор гиперпараметров.
- Кросс-валидация для оценки качества моделей.

### 5. Тестирование и оценка качества
- Предсказание на тестовой выборке (10% данных).
- Расчёт RMSE.
- Целевая метрика достигнута: **RMSE ≤ 48**.

## Анализ остатков модели CatBoost

- **Распределение остатков**:  
  Остатки распределены почти симметрично, но с длинным правым хвостом — это говорит о случаях сильного недооценивания реального значения заказов.

- **Анализ во времени**:  
  Остатки хаотично распределены вокруг нуля, трендов не наблюдается. Присутствуют положительные выбросы.

## Выводы

- Построена рабочая модель прогнозирования количества заказов такси.
- Модель уложилась в заданный порог RMSE, показав высокую точность и стабильность.
- Распределение остатков показывает, что модель хорошо справляется с прогнозом, но есть отдельные случаи недооценивания спроса.

## Рекомендации
- Для улучшения качества модели рекомендуется:
  - Попробовать другие методы борьбы с выбросами.
  - Увеличить количество обучающих данных.
  - Провести дополнительный анализ важности признаков.
- Внедрение данной модели позволит оптимизировать количество водителей в часы пик, повысив уровень клиентского сервиса.
