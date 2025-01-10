github - https://github.com/fuquyoma/Program5/tree/main/ЛР№3

test.pypi - https://test.pypi.org/project/open-weather-LW/0.0/
## Директория
![image](https://github.com/user-attachments/assets/5ef502b2-94fd-4ee4-9d41-24eb46c08eaf)
## Пакет
Пакет был взяят из предыдущей лабораторной работы с API open weather
## Setup
Создаём файлы setup.py и setup.cfg и настраиваем их
### setup.py
```
from setuptools import setup
from pathlib import Path

this_directory = Path(__file__).parent
long_description = (this_directory / "README.md").read_text(encoding='utf-8')

setup(
    name='open-weather_LW',
    version='0.0',
    description='Openweather API',
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/fuquyoma/Program5/tree/main/ЛР№3",
    packages=['open-weather_LW'], 
    author='Artem Gnevnov',
    author_email='gnevnov1996@mail.ru',
    zip_safe=False
)
```
### setup.cfg
```
[egg_info]
tag_build = 
tag_date = 0
```
## Создание дистрибутивных файлов
Выполняем команду
```
python setup.py sdist bdist_wheel
```
У нас появятся папка dist
## Публикация на test.pypi
```
twine upload --repository testpypi dist/*
```
