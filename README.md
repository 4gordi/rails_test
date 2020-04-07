0) Подготовка

 - sudo apt-get install curl //Установка установщика с урлов
 
 - sudo apt-get install git-core build-essential libgdbm-dev libncurses5-dev automake libtool bison libffi-dev nodejs //Установка зависимостей, можно устанавливать каждый отдельно

 1) Установка RVM - Ruby Version Manager
 
 //переходим на сайт rvm.io там будет список команд для установки rvm
 
 - gpg2 --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB  //Копируем GPG ключ

 - \curl -sSL https://get.rvm.io | bash -s stable  //Устанавливаем стабильную версию менеджера
 
 //Если на данном этапе есть ошибка установки ключа, не найдена команда или прочее, устанавливаем gpg2
 
 - sudo apt-get install gnupg2 -y //Команда для установки gpg2
 
 - gpg2 --list-keys //Список установленных ключей
 
 //Затем необходимо проверить файл /.bash_profile в папке /home/user/
 
 - nano ~/.bash_profile
 
 //Если такого файла нет, то его необходимо создать и прописать строчки ниже
 

 [[ -s "$HOME/.profile" ]] && source "$HOME/.profile" # Load the default .profile
 [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into shell session *as a function
 
 
 //После этого можно проверить работу rvm командой
 
 - rvm -v //Команда должна вернуть значение версии rvm
 
 - rvm get stable //Обновление rvm
 
2) Установка Ruby

 - rvm list known //Выведет список всех новых и старых версий ruby на данный момент времени
 
 - rvm install 2.7.0 //Скомпилирует и установит выбранную версию ruby для вашей ситсемы
 
//После установки можно проверить версию

 - ruby -v //Вернет версию установленной ruby

 - rvm list //Покажет список всех установленных версий ruby на данном пк
 
 - rvm use 2.7.0 //Использует выбранную версию в текущий момент

 - rvm use 2.7.0 --default //Использует выбранную версию по умолчанию
 
 - rvm remove 2.7.0 //Удаляет выбранную версию
 
 - gem -v //Проверка версии менеджера библиотек
 
 - gem update --system //Обновление последней версии менеджера библиотек
 
 //Можно создать файл .gemrc и в нем прописать строчки
 
 - cd //Вернуться в домашнюю папку
 
 - nano ~/.gemrc //Создать или открыть файл .gemrc
 
 Прописать " gem: --no-document "//Терминал когда увидит строку gem install ... будет добавлять --no-document что не даст установщику устанавливать мануалы по библиотеке, которые очень много весят
 
 3) Установка Rails
 
 - gem install rails //Установка последней стабильной версии rails

 - gem install rails -v 5.0.0 //Установит конкретную версию rails
 
 - rails -v //Покажет установленную версию rails
 
 - gem list rails //Покажет список установленных библиотек принадлежащих данной версии rails
 
 - gem list //Покажет все установленные библиотеки
 
 - gem install bundler //Установка установщика библиотек
 
 4) Создание первого приложения на rails
 
 - cd //Переход в домашнюю директорию
 
 - rails new blog //Создать новое приложение с название blog
 
 - rails _4.2.7_ new blog //Создание нового приложение более старой версией rails
 
 - rails new blog -T //Создание нового приложение без папок тестов
 
 - cd /blog //Зайти в папку нового приложения
  
 - nano public/index.html //Создание первой тестовой страницы, в ней можно прописать:
 
 
 <!DOCKTYPE html>
 <html lang="ru">
 <head>
    <meta charset="UTF-8">
    <title>Ruby on Rails</title>
 </head>
 <body>
    <h1>Привет от Ruby on Rails!</h1>
 </body>
 </html>

 
 - bundle exec rails s //Запуск сервера rails
 
 //После запуска сервера нужно в браузере зайти на:
 
 localhost:3000 //или
 
 127.0.0.1:3000 //Должна появиться наша тестовая страница
 
 5) Установка и настройка GIT
 
 //GIT мы установили ранее с азвисимостями git-core, сейчас необходимо настроить под наш аккаунт для это прописываем:
 
 - git config --global user.name '4gordi' //Прописываем логин
 
 - git config --global user.email '4gordi@gmail.com' //Прописываем почту
 
 //Находясь в папке с новым приложением rails нужно ввести
 
 - cd /blog //Убедитесь что вы в папке с приложением
 
 - git init //Создаст репозиторий в текущей папке и будет отслеживать изменения проекта
 
 - git status //Покажет текущее состояние проекта: новые файлы, изменения в файлах и.т.д
 
 - git add . //Добавит все изменения данных файлов в очередной коммит
 
 - git add *.html //Добавит изменения только файлов с расширением .html
 
 - git add index.* //Добавит изменения только файлов с названием index.
 
 - git commit -am "Initial commit" //Добавляет комментарий к изменениям в проекте
 
 //Все команды сверху актуальны для локального репозитория (который находится на вашем ПК)
 //Ниже команды для создания удаленного репозитория
 
 - sudo curl -u 'USER_NAME' https://api.github.com/user/repos -d'{"name":"demo"}' //Вместо USER_NAME необходимо вписать логин, а вместо demo название репозитория
 
 - sudo git remote add origin https://github.com/USER_NAME/demo.git
 
 - git push -u origin master

 - git fetch origin //Показывает информацию об изменениях на удаленном сервере origin
 
 - git pull origin //Сливает изменения с удаленного сервера origin в локальный сервер
 
 - git push origin //Сливает изменения с локального сервера на удаленный origin 
 

 6) Установка хостинга HEROKU
 
 //Необходимо зарегестрироваться на сайте heroku
 
 //Установка heroku cli или heroku toolbelt
 
 - curl https://cli-assets.heroku.com/install.sh | sh //Скачать и установить heroku cli
 
 - heroku --version //Проверка версии heroku
 
 //Если есть ошибки на этом моменте можно прописать права доступа к папке с кешом heroku
 
 - sudo chown -R 4gordi ~/.cache/heroku //Сделать пользователя владельцем пути
 
 //Переходим в папку с проектом
 
 - cd blog/
 
 - heroku login //Авторизация в heroku
 
 - heroku create //Создает новое приложение heroku
 
 //Нужно изменить новые зависимости
 
 //добавить строчки:
 
 group :production do
    gem 'pg'
 end
 
 //Перенести gem 'sqlite3' в :development
 
 //После этого мы можем выполнить
 
 - bundle install --without production
 
 - git status
 
 - git add .
 
 - git commit -am "sqlite3 fixed for heroku"
 
 - git push heroku master //Залить проект на heroku в ветку master
 
 //Если прошло с ошибкой, необходимо выполнить:
 
 - git checkout -b fixes
 
 //Удалить файл Gemfile.lock
 //
 
 - bundle update
 
 - bundle install --without production
 
 - git add .
 
 - git commit -am "Update files for heroku v2"
 
 - git checkout master
 
 - git merge fixes
 
 - git push -f heroku master
  
 - heroku open //Откывает залитый проект
 
 - heroku apps:rename newname //Переименовать стандартное имя сайта heroku на свое

 - heroku apps:rename newname --app oldname //Переименовать уже существующий репозиторий на heroku
