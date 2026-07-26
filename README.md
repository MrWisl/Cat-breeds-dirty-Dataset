# 🐱 Cat Breeds Dataset Cleaning & Analysis
Репозиторий содержит Jupyter Notebook с полным циклом очистки, обработки и импутации "недостоверных" и пропущенных данных о породах кошек. 
* **Исходный датасет**: [Cat Breeds Dataset на Kaggle](https://www.kaggle.com/datasets/joannanplkrk/its-raining-cats?select=cat_breeds_dirty.csv)
В процессе работы исходный набор данных избавляется от текстового шума, некорректных значений (отрицательный возраст, невалидные категории) и пропусков с помощью алгоритмов на основе эвристик и евклидова расстояния
---
## 🛠 Технологический стек
* **Язык**: Python 3
* **Библиотеки**: `pandas`, `numpy`
---
## 📊 Основные этапы обработки данных
### 1. Первичная очистка текста и стандартизация
* Приведение текстовых строк к единому регистру (`.str.title()`, `.str.capitalize()`)
* Удаление невалидных категориальных значений (мусорные текстовые ответы в полях окраса, цвета глаз, разрешения выходить на улицу и названия стран).
* Фильтрация отрицательных значений для физических показателей (возраст, вес, длина).
### 2. Восстановление возраста
* Расчет пропущенных значений в годах (`Age_in_years`) на основе месяцев (`Age_in_months`) и наоборот.
### 3. Определение пола и породы через Евклидово расстояние
* Вычисление центроидов по физическим параметрам (`Weight`, `Body_length`).
* Восстановление пропущенного пола с учетом полового диморфизма породы и расстояния до центроидов.
* Классификация неизвестной породы по ближайшему центроиду в пространстве физических характеристик.
### 4. Гео-импутация (Координаты и Страна)
* Восстановление названий стран по наиболее часто встречающимся координатам (мода).
* Заполнение пропущенных широты (`Latitude`) и долготы (`Longitude`) средними значениями пространственных кластеров внутри страны.
### 5. Импутация категориальных и численных признаков
* Заполнение оставшихся численных пропусков средними значениями внутри групп `[Breed, Gender]`.
* Заполнение категориальных пропусков модой внутри групп `[Breed, Gender]`.
* Финальная очистка записей без ключевой информации.
---
## 🚀 Как запустить
1. **Клонируйте репозиторий**:
   ```bash
   git clone https://github.com/MrWisl/Cat-breeds-dirty-Dataset.git
   cd папка куда склонирован репозиторий
2. **Скачайте датасет**:
   Загрузите исходный файл cat_breeds_dirty.csv с Kaggle и поместите его в папку DataSet/ (или укажите свой путь в ноутбуке).
3. **Установите зависимости**:
   ```bash
   pip install pandas numpy
   
   ```
 4. **Запустите Jupyter Notebook**:
     ```bash
     jupyter notebook
   
     ```
## 📁 Структура проекта
```text
├── cat_cleaning.ipynb           # Основной ноутбук с обработкой данных
└── README.md                    # Описание проекта
```
## 📈 Результаты cleaning-процесса

| Показатель | До очистки | После очистки |
| :--- | :--- | :--- |
| **Всего строк** | 1102 | 1090 |
| **Уникальные породы** | Нестандартизированные / с ошибками | Очищены и приведены к Angora, Maine Coon, Ragdoll |
| **Гео-данные** | Пропуски / Ошибки | Заполнены кластеризацией |

## English language:
# 🐱 Cat Breeds Dataset Cleaning & Analysis
This repository contains a Jupyter Notebook with a complete pipeline for cleaning, processing, and imputing unreliable and missing data on various cat breeds.
* **Original Dataset**: [Cat Breeds Dataset on Kaggle](https://www.kaggle.com/datasets/joannanplkrk/its-raining-cats?select=cat_breeds_dirty.csv)
During the process, noise, invalid records (such as negative age values or improper categories), and missing fields are handled using rule-based heuristics and Euclidean distance algorithms.
---
## 🛠 Tech Stack
* **Language**: Python 3
* **Libraries**: `pandas`, `numpy`
---
## 📊 Key Data Processing Steps
### 1. Initial Text Cleaning & Standardization
* Converting string values to a unified case format (`.str.title()`, `.str.capitalize()`).
* Removing invalid categorical values (garbage text inputs in coat color, eye color, outdoor access permissions, and country names).
* Filtering out negative values for physical metrics (age, weight, body length).
### 2. Age Recovery
* Calculating missing values in years (`Age_in_years`) based on months (`Age_in_months`) and vice versa.
### 3. Gender & Breed Imputation via Euclidean Distance
* Computing centroids for physical parameters (`Weight`, `Body_length`).
* Imputing missing gender values considering breed sexual dimorphism and distance to centroids).
* Classifying unknown breeds by identifying the nearest centroid in the physical feature space.
### 4. Geo-Imputation (Coordinates & Country)
* Recovering missing country names based on the most frequent coordinates (mode).
* Filling missing latitude (`Latitude`) and longitude (`Longitude`) values using the mean of spatial clusters within each country.
### 5. Categorical & Numerical Feature Imputation
* Filling remaining numerical missing values with group means based on `[Breed, Gender]`.
* Filling missing categorical values with the group mode based on `[Breed, Gender]`.
* Final cleanup of records missing critical context.
---
## 🚀 How to Run
1. **Clone the repository**:
   ```bash
   git clone https://github.com/MrWisl/Cat-breeds-dirty-Dataset.git
   cd the folder where the project was copied to
  2. **Download the dataset**:
     Download the original cat_breeds_dirty.csv file from Kaggle and place it in the project root directory (or update the file path directly in the notebook).
  3. **Install dependencies**:
     ```bash
     pip install pandas numpy
   
     ```
 4. **Launch Jupyter Notebook**:
     ```bash
     jupyter notebook
   
     ```
## 📁 Project Structure
```text
├── cat_cleaning.ipynb           # Main notebook containing data processing steps
└── README.md                    # Project documentation
```
## 📈 Cleaning Process Results

| Metric | Before Cleaning | After Cleaning |
| :--- | :--- | :--- |
| **Total Rows** | 1102 | 1090 |
| **Unique Breeds** | Unstandardized / Contains errors | Cleaned and mapped to Angora, Maine Coon, Ragdoll |
| **Geo Data** | Missing values / Spatial errors | Imputed using spatial clustering |

## Примечание:
Данный проект был создан в исключительно образовательных целях, и не приследует идей воровства, присваивание чужих заслуг и тому подобное, если возникнут какие-то вопросы, претензии и тому подобное вы можете связаться со мной:
Почта: questionsanswer16@gmail.com

## Note:
This project was created for educational purposes only, and does not promote the ideas of theft, plagiarism, or similar actions. If you have any questions, concerns, or suggestions, please contact me:
Email: questionsanswer16@gmail.com
