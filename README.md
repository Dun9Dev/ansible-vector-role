# Роль Vector

Ansible роль для установки и настройки Vector — высокопроизводительного конвейера данных для observability.

## Требования
- Ansible версии 2.10 или выше
- Целевой хост с systemd

## Переменные роли
- `vector_version` - версия Vector (по умолчанию: "0.34.1")
- `vector_architecture` - архитектура (по умолчанию: "x86_64")
- `vector_install_dir` - директория установки (по умолчанию: "/opt/vector")
- `vector_config_dir` - директория конфигурации (по умолчанию: "/etc/vector")

## Зависимости
Отсутствуют.

## Пример playbook
hosts: vector
roles:

vector-role

## Лицензия
MIT

## Информация об авторе
Создано в учебных целях
