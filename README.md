# Обновление сертификатов в CommuniGate Pro

Этот скрипт автоматически обновляет SSL-сертификаты для нескольких доменов в сервере **CommuniGate Pro** (CGP) с использованием сертификатов **Let's Encrypt**. Также он отправляет уведомления с логами обновления на email.

## 📌 Функциональность
- Обновляет **ключ, сертификат и цепочку сертификатов** для указанных доменов в CGP.
- Логирует процесс обновления в `/var/log/update_cgp_cert.log`.
- **Автоматически отправляет email-уведомления** с итогами работы.
- Работает с несколькими доменами одновременно.
- Может быть добавлен в `cron` для автоматического обновления сертификатов.

## 🔧 Установка и использование
### 1. Клпируем скрипт
```
 wget https://github.com/saym101/sysadmin_repo/raw/refs/heads/main/update_cgp_cert.sh

```

### 2. Настройка переменных
Перед использованием необходимо отредактировать переменные в скрипте:
```bash
DOMAINS=("stpserver.ru talabsk.ru zaweru.ru")  # Укажите свои домены
POSTMASTER_NAME="postmaster@stpserver.ru"
POSTMASTER_PASSWORD="Brqada123!"  # Укажите свой пароль
NOTIFICATION_EMAIL="postmaster@stpserver.ru"
IP_CGP_SERVER="127.0.0.1"
CLI_PORT="8100"
SMTP_SERVER="127.0.0.1:25"
```

### 3. Даем права на выполнение
```bash
chmod +x update_cgp_cert.sh
```

### 4. Запуск скрипта вручную
```bash
./update_cgp_cert.sh
```

### 5. Автоматизация через CRON
Добавьте в `crontab -e` строку:
```bash
0 3 * * * /path/to/update_cgp_cert.sh >> /var/log/update_cgp_cert_cron.log 2>&1
```
Этот cron-запуск обновит сертификаты каждый день в 3:00 ночи.

## 📜 Логи и отладка
После выполнения скрипта лог-файл можно найти здесь:
```bash
cat /var/log/update_cgp_cert.log
```

## 🔒 Безопасность
- **Не храните пароль в коде!** Лучше использовать переменные окружения или хранить пароль в защищённом файле.
- Убедитесь, что **`postmaster` имеет доступ к API CommuniGate Pro**.

## 🎯 TODO
- [ ] Автоматическое обновление сертификатов через `certbot`
- [ ] Поддержка HTTPS-запросов для API CommuniGate Pro
- [ ] Добавление ротации логов

---

📌 Автор: [Ваше Имя](https://github.com/your-profile) | 🚀 [GitHub Repo](https://github.com/your-repo/update-cgp-cert)

