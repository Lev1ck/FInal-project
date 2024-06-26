# Final-project
Финальный проект по курсу "Наука о данных" 2024
# Идея проекта
Я всегда хотел начать профессионально играть на бирже, чтобы уметь предсказывать цену акций. Недавно на курсе "Введение в Финансы" я ознакомился с таким активом, как индекс S&P 500, и меня заинтересовало, возможно ли с помощью макроэкономических показателей понимать поведение данного индекса. Кроме того, S&P 500 является основопологающим активом современного финансового сектора, поэтому хочется понять получше его структуру, проанализировать компании, которые в него входят, чтобы это помогло помочь прогнозировать поведение индекса.
# Цель проекта
Проанализировать индекс S&P 500 с точки зрения акций, составляющих его, а также найти взаимосвязь между ним и макропоказателями.
# Используемые технологии
1. Pandas - работа с основным датафреймом, группировка, срезы, использование дополнительных функций.
2. Web-scrapping - использование библиотеки requests для парсинга данных с yahoo finance, BeautifulSoup чтобы парсить с википедии
3. API - поднадобился, чтобы использовать библиотеку FRED и парсить данные оттуда, а также использовал json, чтобы визаулизировать карту США.
4. Визуализация данных - использовал библиотеку matplotlib, seaborn, и plotly для серьёзной детализации при работе с геоданными.
5. Geopandas - использовался, чтобы узнать координаты городов, в которых находятся штаб-квартиры компаний, входящих в индекс S&P 500.
6. SQL - использовался чтобы упорядочить корреляцию между активом и индексом S&P 500, а также, чтобы найти самый волатильный актив, входящий в индекс
7. Numpy - в основном использовался для расчёта внутренних функций, также помогал при работе с dataframe.
8. Scipy - использовался при работе над статистическим тестом, чтобы найти распределение определенных фичей.
9. Регулярные выражения - использовались, чтобы привести данные по местоположение штаб-квартир в должный вид для работы с geopandas.
10. Использовал линейную регрессию, регрессию с регуляризацией, а также KNN для регрессии из sklearn, чтобы предсказывать поведение индекса, а также найти значимые признаки.
# Описание признаков
Здесь я хочу ввести в небольшой экскурс по макроэкономическим параметрам, которые я рассматривал в ходе своей работы.

1. **Global uncertainty index** - это метрика, которая измеряет уровень неопределенности в мировой экономике.Чем выше уровень индекса, тем больше неопределенности и рисков в мировой экономике. Это может влиять на решения инвесторов, бизнес-лидеров и политиков, так как высокий уровень неопределенности может привести к осторожности и ограничениям в инвестициях и росте экономики. Должен быть отрицательно скоррелирован с индексом.
2. **Безработица** - это состояние, когда люди в возрасте, способные и готовые работать, не имеют работы и ищут её. Данный показатель рассматривается в США. Должен быть отрицательно скоррелирован с индексом.
3. **Индекс потребительских цен (cpi)** - обычно рассчитывается путем отслеживания изменений цен на определенную "корзину" потребительских товаров и услуг, которые типично покупаются домашними хозяйствами. Эта корзина может включать продукты питания, жилье, транспорт, медицинские услуги, образование и другие предметы и услуги, которые потребители регулярно покупают. На основе его делаются выводы про уровень инфляции в стране. В проекте также рассматривает показатель для США. Должен быть положительно скоррелирован с индексом.
4. **Реальная процентная ставка** (interest rate) США - процентные ставка, которая определяется Федеральным резервным банком США  и влияет на уровень процентных ставок на рынке краткосрочного кредитования между банками. Должна быть отрицательно скоррелирована с индексом.
5. **Торговый баланс (balance trade)** - это показатель, используемый для измерения разницы между экспортом и импортом товаров в экономике страны за определенный период времени. Рассматривается в рамках США. Должен быть отрицательно скоррелирован с индексом.
6. **Долг (debt)** -  сумма денег, которую правительство должно в виде кредитов или выпуска облигаций для финансирования своих расходов, таких как социальные программы, оборонные расходы или инфраструктурные проекты. Рассматривается в рамках США. Должен быть положительно скоррелирован с индексом.
7. **Индекс активности (activity index)** - нулевое значение индекса указывает на то, что национальная экономика расширяется историческими темпами роста; отрицательные значения указывают на рост ниже среднего; а положительные значения указывают на рост выше среднего. Рассматривается на уровне США. Должен быть положительно скоррелирован с индексом.
8. **Розничные продажи (retail sailes)** - это общая сумма денег, полученная от продажи товаров или услуг конечным потребителям через розничные точки продаж, такие как магазины, супермаркеты, интернет-магазины и другие розничные предприятия. Рассматривается в рамках США. Должен быть положительно скоррелирован с индексом.
9. **Реальный эффективный обменный курс (Real Broad Effective Exchange Rate)** -  мера стоимости валюты по отношению к средневзвешенному значению нескольких иностранных валют, скорректированное на уровень инфляции. Рассматривается в рамках США. Должно быть полодительно скоррелировано с индексом.
10. **Индекс цен на жилье (house price index)** - это статистический показатель, который отражает изменения в ценах на жилую недвижимость. Он используется для оценки тенденций на рынке недвижимости, а также для анализа динамики стоимости жилья. Должен быть полодительно скоррелирован с индексом.

# Описание хода работы
Сбор данных по основным акциям, входящим в индекс, а также информация по макропоказателям. Затем, мы визаулизируем данные, чтобы понять, как устроен индекс, а также выявить зависимости между ним и признаками. Таким образом, проверяем соотносится ли наше научное понимание и реальные данные. После этого, чтобы понять как устроен индекс, работаем с геоданными и sql. И, наконец, заверщающий этап - работа с моделями машинного обучения - отбор признаков, выявление самых значимых - и оценка их распределения.

# Итоги работы
У меня получилось выявить основные макроэкономические признаки, с помощью которых можно предсказывать движение индекса S&P 500. Кроме того, я смог представить чёткую структуру индекса, выявив некоторые закономерности для акций, которые входят в него, показав их основные характеристики, и связь с таргетом. 

p.s при отправке проекта заметил, что на гитхабе высвечиваются не все графики, поэтому лучше смотреть в colabe
