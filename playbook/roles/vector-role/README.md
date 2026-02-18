# Ansible role: Vector

Роль для установки и настройки [Vector](https://vector.dev/) - инструмента для сбора и обработки логов.

## Требования

- Ansible 2.14 или выше
- Поддерживаемые ОС:
  - Ubuntu 22.04
  - Ubuntu 24.04
  - Oracle Linux 8

## Переменные

| Переменная | Значение по умолчанию | Описание |
|------------|----------------------|----------|
| `vector_version` | `0.34.1` | Версия Vector для установки |
| `vector_config_dir` | `/etc/vector` | Директория для конфигурации |
| `skip_vector_stop` | `false` | Пропустить остановку Vector (для тестов) |

## Зависимости

Нет зависимостей от других ролей.

## Пример playbook

```yaml
- hosts: all
  roles:
    - role: ansible-vector-role
      vector_version: "0.34.1"
```

## Тестирование

### Настройка окружения

```bash
# Установка зависимостей
pip install -r requirements.txt

# Установка коллекций (если проблемы с Galaxy)
ansible-galaxy collection install git+https://github.com/containers/ansible-podman-collections.git
ansible-galaxy collection install git+https://github.com/ansible-collections/ansible.posix.git
```

### Запуск тестов molecule

```bash
# Тестирование с драйвером podman
molecule test -s podman

# Тестирование с драйвером docker (совместимость)
molecule test -s compatibility
```

### Запуск тестов tox

```bash
# Установка tox
pip install tox

# Запуск всех тестов
tox
```

## Сценарии тестирования

- **default** - базовый сценарий с драйвером docker
- **podman** - облегчённый сценарий с драйвером podman
- **compatibility** - сценарий для тестирования на разных ОС

## Решённые проблемы

| Проблема | Решение |
|----------|---------|
| Отсутствие curl в контейнере | Добавлена установка curl в prepare.yml |
| Ошибка "Stop Vector if running" | Добавлена переменная `skip_vector_stop` |
| Проблемы с доступом к Galaxy | Установка коллекций из GitHub |
| Отсутствие драйвера podman | Установлен `molecule-plugins[podman]` |

## Версионирование

- **v0.1.0** - базовая установка Vector
- **v0.2.0** - добавлены тесты molecule и tox

## Лицензия

MIT

## Автор

Shestovskikh Daniil






P.S. Скриншоты с успешным выполнением команд [тут](https://github.com/Dun9Dev/ansible-vector-role/tree/feature/molecule/playbook/image)
