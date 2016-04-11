# go-vk-random-pin

Heroku clock-процесс на Go для закрепление случайного поста на стене VK.

### Установка:

```
go get github.com/winogradoff/go-vk-random-pin
```

### Запуск:

```
go-vk-random-pin
```

### В переменных окружения (Config Variables для Heroku) должны быть заданы следущие значения:

```
VK_AUTH_TOKEN = <токен авторизации в VK>
VK_SCHEDULER_INTERVAL_SECONDS = <интервал в секундах>
VK_PROFILE_URL = <ссылка на профиль (http://vk.com/user)>
```

### Токен авторизации можно получить при переходе по следующему URL:

```
https://oauth.vk.com/authorize?client_id=<client_id>&scope=wall,offline&redirect_uri=https://oauth.vk.com/blank.html&display=page&v=5.29&response_type=token
```

где `<client_id>` — идентификатор приложения VK.

### Команда выполняется каждые VK_SCHEDULER_INTERVAL_SECONDS секунд:

```go
gocron.Every(interval).Seconds().Do(task, authToken, profileUrl)
<-gocron.Start()
```

### Зависимости:

* [goCron — a Golang Job Scheduling Package](https://github.com/jasonlvhit/gocron)
* [Jason — easy-to-use JSON library for Go](https://github.com/antonholmquist/jason)
* [vk_wrapper — Golang api wrapper for most popular Russian social network vk.com](https://github.com/bogdansolomykin/vk_wrapper)