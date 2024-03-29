**ПРОЕКТ: PIXEL-WISE-EMBEDDING** ([презентация](https://docs.google.com/presentation/d/1IopWWRSgE1p5IqQ6hsQ7Cg6RaduEW_UJFlEfOeZWWaA/edit?usp=sharing)) 

//**ОТКРЫТ НАБОР:** для записи в проект, пишите [Александру](https://t.me/ASRomahin) или [Евгении](https://t.me/evsotnikova)//

**Руководитель:** [Ромахин Александр Сергеевич](https://github.com/asromahin), Computer Vision Team Lead в компании ЕВРАЗ. 

**Описание:** Проект направлен на исследование возможностей получение эмбеддингов для пикселей изображений, по которым можно будет делать аналитику следующего толка: поиск похожих объектов на разных изображениях, автоматическая аннотация изображений.
 
**Гипотеза о результате:**
Мы знаем, как обучаются эмбединги для изображений, берём классификатор, отрубаем классифицирующий слой и остается слой, который из себя представляет сжатое представление об изображении. Для изображения например размером 256х256 получается вектор в 1024, который описывает контекст изображения. Но мы попробуем получить контекстное представление не для всего изображения, а для каждого отдельного пикселя. Т.е. пиксели, одинаковых объектов должны быть близки друг к другу в пространстве эмбедингов, а пиксели разных объектов - далеки. Тем самым мы получаем даже для пикселей объектов, которых не было в обучении, какое-то представление в этом пространстве, с которыми можно оперировать различными способами. На данный момент есть понимание применение этой технологии для решения следующих задач:

1) Поиск похожих объектов между изображениями. Может быть применено для неразмеченных датасетов. Парсим из интернета по текстовому запросу 1000 штук нового объекта, прогоняем эмбедером и смотрим самый часто-встречаемый вектор, если система работает правильно - это будет как раз интересующий нас объект

2) Интерактивная сегментация - типичные подходы для ускорения разметки сегментации, это модели для интерактивной сегментации, т.е. на вход помимо изображения подаётся ввод пользователя, например клик в определенной области, а на выходе - сегментационная маска, на который кликнул пользователь. Получается в этом случае на каждый новый клик необходимо срабатывать модели заново, что замедляет процесс и является проблемой для удобного пользования. Получение эмбединга для каждого пикселя позволяет не прогонять модель каждый раз, а сделать это лишь один раз, а затем уже просто оперировать этими эмбедингами и проводить над ними операции, которые могут осуществляться на стороне клиента, т.к. не являются вычислительно дорогими.

3) Использования как condition для обучения GANов. Если мы имеем модель, которая выдаёт релевантные эмбединги для пикселей, это может быть сильным признаком для обучения GAN моделей, благодаря которому модель конкретно на каждом пикселе сможет понимать, что это далеко от того, что бывает на реальных снимках.

4) Обратная задача - т.е. если мы можем обучить эмбединг, то мы можем и эмбедингу присвоить изображение. Тем самым мы можем манипулировать эмбедингами, смещать их и двигать, и получать видоизмененное изображение как по текстура, так и по содержанию, что позволит, например, делать интересные аугментации.

На выходе ожидаем готовые пайплайны для обучения, сравнение подходов, применение в озвученных задачах и сравнение с другими методами, в которых могут быть применены эти модели. Всё будет оформлено в репозитории.


**Пре-реквизиты:** Python, Pytorch или Keras(TensorFlow), Сегментация изображений, Классификация, Metric Learning

**Чему можно научиться:** 
- Строить и проверять гипотезы
- Более глубокое понимание принципов работы моделей
- Разработка специфичных слоев для реализации конкретных задач
- Корректно сравнивать алгоритмы между собой
- Разработка полноценного инструмента, которым смогут пользоваться другие специалисты для решения своих задач
- Командная разработка
