# ML_homework1
Результаты выполнения ДЗ по теме Regression with inference base

### Часть 1. EDA датасета с ценами на автомобиль и их признаками 
- [x] - оценить входные данные на трейн и тест, определить какие столбцы необходимо предобработать (те, что имеют строковый формат в виде значения с единицами измерения)
- [x] - предобработка столбцов с единицами измерения - удаление единиц измерения, в столбце остались только числовые значения
- [ ] - предобработка столбца torque - не удалась, но и в базовом ДЗ не обязательна
- [x] - определить наличие дублей и пропусков - пропуски заполнить медианным значением по трейну, дубли удалить
- [x] - числовые значения привести к типу данных int и float
- [x] - построить попарные графики зависимости параметров и целевой переменной - определить корреляцию (подтвердить данный факт построением тепловой карты и матрицей коэффициентов корреляции). С таргетом (цена автомобиля) наиболее всего коррелирует признак max power.
- [x] - дополнительно оценила распределение тагрета и пришла к выводу, что его лучше всего логарифировать для полуечния нормального распределения
      
### Часть 2. Построение моделей 
- [x] - обучение и предикт обычной модели линейной регрессси на вещественных признаках:
|---|---|
|MSE train|116873522067|
|MSE test |254290302631|
|r2 train|0.59226|
|r2 test|0.55762|
- [x] - применеине StandartScaler - не дало улучшений по показателям метрик
- [x] - применение модели с L1-регуляризацией и проведения кросс-валидации на 10 фолдах: был определен оптимальный гиперпараметр альфа 26609, занулилось три веса (самые маленькие по модулю изначально) - mileage,	engine, seats
      |---|---|
|MSE train|116873522067|
|MSE test |254290302631|
|r2 train|0.59226|
|r2 test|0.55762|
- [x] - применение модели ElasticNet c кросс-валидацией на 10 фолдах для подбора гиперпараметров альфа и l1-ratio (комбинация параметров L1 и L2 регуляризации). Удалось подобрать лучшие параметры, но качество модели на разбиении на трейн и тест не улучшилось
### Часть 3. Построение модели на вещественных и категориальных фичах
- [x] - применен метод OHE для обработки категориальных признаков (обучен на трейне и применен к трейн и тесту)
- [x] - построена модель Ridge, проведена кросс-валидация для определения лучшего гиперпараметра альфа (630) - метрики улучшились на трейне, но разрыв между трейн и тест стал больше
### Часть 4. Финальные решения по модели
- [x] - создана бизнес-метрика, которая среди всех предсказанных цен на авто показывает долю прогнозов, отличающихся от реальных цен на эти авто не более чем на 10%
- [x] - на ее основании определено, что лучшая модель - это ElasticNet c подобранными гиперпарамтерами выше
- [x] - модель со всеми характеристиками сохранена в pkl файл
### Часть 5. FastAPI

#### ВЫВОДЫ И ПРОБЛЕМЫ
1)

