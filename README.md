# situ-devops-04 Лаб 4.

## Задача
Создать плейбук и роль Nginx Vhost.
Роль должна устанавливать на целевой хост nginx и активировать vhost c заданным именем.
Для vhost использовать j2 шаблон индексного файла и конфига.
Родительский плейбук должен вызывать роль и список vhost передавать через переменную уровня плей в цикле.

Структура проекта
```
├── inventory
├── playbook.yml
└── roles
    └── nginx_vhost
        ├── tasks
        │   └── main.yml
        ├── templates
        │   ├── index.html.j2
        │   └── vhost.conf.j2
        └── handlers
            └── main.yml
```

## Запуск плейбука
```
ansible-playbook -i inventory playbook.yml
```

## Проверка
```
sergey@situ-vm-1:~/situ-devops-04$ curl site1.local
<!DOCTYPE html>
<html>
<head>
    <title>site1.local</title>
</head>
<body>
    <h1>site1.local</h1>
    <p>Configured by Ansible</p>
</body>
</html>sergey@situ-vm-1:~/situ-devops-04$ curl site2.local
<!DOCTYPE html>
<html>
<head>
    <title>site2.local</title>
</head>
<body>
    <h1>site2.local</h1>
    <p>Configured by Ansible</p>
</body>
</html>
```
