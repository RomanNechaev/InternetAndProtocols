# DNS Кэш-Сервер

Простой DNS кэш-сервер с поддержкой кэширования запросов и перенаправлением на внешний DNS-сервер.

## Возможности

- Кэширование DNS-запросов для ускорения ответов
- Поддержка различных типов DNS-записей (A, NS, CNAME, MX и др.)
- Перенаправление запросов на внешний DNS-сервер
- Многопоточная обработка запросов
- Защита от циклических запросов

## Использование

Запуск сервера:
```bash
python3 dns.py -i <IP_forwarder> -P <порт> -p <порт_forwarder>
```

Параметры:
- `-i` - IP-адрес DNS forwarder'а (обязательный)
- `-P` - порт для вашего DNS сервера (по умолчанию: 53)
- `-p` - порт DNS forwarder'а (по умолчанию: 53)

Примеры:
```bash
# Запуск с Google DNS (требует sudo для порта 53)
sudo python3 dns.py -i 8.8.8.8 -P 53 -p 53

# Запуск с нестандартным портом (не требует sudo)
python3 dns.py -i 8.8.8.8 -P 5354 -p 53
```

## Тестирование

Проверка работы сервера:
```bash
dig @localhost -p <порт> example.com
```

## Структура проекта

- `dns.py` - основной файл запуска сервера
- `resolver.py` - логика разрешения DNS-запросов
- `cache.py` - реализация кэширования
- `server.py` - базовый класс сервера
