# README: Проект с использованием Ansible для настройки хостов
## Структура проекта
```
├── ansible.cfg
├── group_vars
│   └── all.yml
├── inventory
│   └── hosts.ini
├── playbook.yml
└── vars
    └── packages.yml
```
## Описание проекта

Этот проект использует Ansible для автоматической настройки и управления удалёнными хостами. В рамках проекта:

1. На Control VM установлен Ansible.

2. На целевом хосте создаются пользователи и настраиваются SSH-ключи для безпарольного подключения.

3. Плейбук обновляет пакеты и устанавливает утилиты, такие как net-tools, curl, и nginx. Также конфигурируется firewall с использованием UFW.

## 1. Создание пользователя и ssh ключей
На Control VM и целевом хосте создаём пользователя ansible-user для подключения к целевому хосту.

### Генерация SSH-ключа:
На Control VM:

```
sudo -u ansible-user ssh-keygen -t rsa -b 4096 -f /home/ansible-user/.ssh/vk
```

### Копирование публичного ключа на целевой хост:

```
sudo -u ansible-user ssh-copy-id -i /home/ansible-user/.ssh/vk.pub ansible-user@[ip]
```

## 2. Запуск Ansible
### Копируем репозиторий
```
git clone https://github.com/JustKirill1/ansible
```
### Запускаем playbook в целевой директории

```
sudo ansible-playbook -i inventory/hosts.ini playbook.yml
```
Если требуется указать пароль от пользователя на целевом хосте, добавляем флаг --ask-become-pass

```
sudo ansible-playbook -i inventory/hosts.ini playbook.yml --ask-become-pass
```
