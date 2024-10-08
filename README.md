
# Load Testing with Locust

## Описание проекта

Этот проект демонстрирует мои навыки в области нагрузочного тестирования веб-приложений и API с использованием инструмента **Locust**. В рамках этого проекта я создал сценарий нагрузки, который имитирует поведение пользователей, взаимодействующих с веб-приложением. Этот тест помогает оценить, как приложение справляется с большой нагрузкой и какие параметры производительности (например, время отклика) могут нуждаться в оптимизации.

## Цель проекта

Основная цель проекта — научиться и продемонстрировать умение создавать и проводить нагрузочные тесты с помощью Locust. Я создал простой сценарий, который имитирует действия пользователей, посещающих разные страницы веб-приложения, и измерил, как сервер справляется с увеличением числа одновременных пользователей.

## Используемые технологии

- **Python 3.10+**: Основной язык программирования для написания сценариев.
- **Locust**: Инструмент для проведения нагрузочного тестирования, написанный на Python.

## Как запустить проект

### 1. Установка Python

Прежде всего, убедитесь, что у вас установлен Python версии 3.10 или выше. Если Python не установлен, вы можете скачать его с [официального сайта Python](https://www.python.org/downloads/).

### 2. Клонирование репозитория

Клонируйте этот репозиторий на свой компьютер:

```bash
git clone https://github.com/Vasovsky/load-testing.git
cd load-testing
```

### 3. Создание и активация виртуальной среды

Создайте виртуальную среду, чтобы изолировать зависимости проекта:

1. Создайте виртуальную среду:
   ```cmd
   python -m venv venv
   ```

2. Активируйте виртуальную среду:
   ```cmd
   venv\Scripts\activate
   ```

### 4. Установка зависимостей

После активации виртуальной среды установите все необходимые зависимости:

```bash
pip install -r requirements.txt
```

### 5. Запуск нагрузочного теста

Чтобы запустить нагрузочный тест, выполните следующую команду:

```bash
locust -f tests/locustfile.py
```

После этого откройте браузер и перейдите по адресу [http://localhost:8089](http://localhost:8089), чтобы открыть интерфейс Locust.

### 6. Настройка и запуск теста

В интерфейсе Locust:
- В поле **Number of users to simulate** укажите количество пользователей, которых вы хотите симулировать.
- В поле **Spawn rate** укажите скорость создания новых пользователей.
- В поле **Host** укажите базовый URL вашего приложения, например, `http://127.0.0.1:5000`.
- Нажмите **Start swarming**, чтобы начать тестирование.

### 7. Остановка теста

Чтобы остановить Locust, выполните следующие шаги:
- В интерфейсе Locust нажмите кнопку **Stop**.
- Или перейдите в командную строку и нажмите `Ctrl + C`, чтобы завершить работу Locust.

## Как это работает

Я разработал сценарий нагрузки, который симулирует поведение пользователей, посещающих страницы веб-приложения. В тесте определены следующие задачи:

1. **Главная страница**: Пользователь посещает главную страницу (`/`).
2. **Страница "О нас"**: Пользователь переходит на страницу "О нас" (`/about`).

### Пример сценария

```python
from locust import HttpUser, TaskSet, task, between

class UserBehavior(TaskSet):

    @task(1)
    def index(self):
        self.client.get("/")

    @task(2)
    def about(self):
        self.client.get("/about")

class WebsiteUser(HttpUser):
    tasks = [UserBehavior]
    wait_time = between(1, 3)
```

Этот сценарий описывает поведение пользователей, которые переходят между двумя страницами веб-приложения с различной частотой.

## Почему это важно

Проведение нагрузочных тестов помогает выявить узкие места в производительности приложения до того, как оно будет развернуто в продуктивную среду. Это помогает предотвратить возможные проблемы, связанные с производительностью, и улучшить качество обслуживания пользователей.

## Заключение

Этот проект дал мне возможность глубже изучить методы нагрузочного тестирования и получить ценный опыт работы с Locust. Я уверен, что эти навыки помогут мне в будущих проектах, где производительность веб-приложений будет критически важна.

## Контакты

Если у вас возникли вопросы или предложения, пожалуйста, свяжитесь со мной по электронной почте: [mikeglukharev@gmail.com](mailto:mikeglukharev@gmail.com). Также вы можете найти другие мои проекты на [моем GitHub профиле](https://github.com/Vasovsky).

