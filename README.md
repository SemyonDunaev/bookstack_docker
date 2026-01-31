# BookStack Home Server Deployment / BookStack на Домашнем Сервере

[English](#english) | [Русский](#russian)

---

<a name="english"></a>
## 🇬🇧 English

Docker Compose file for deploying [BookStack](https://www.bookstackapp.com/) using Docker Compose, MariaDB, Caddy, and No-IP (if no static IP is available).

BookStack seemed like a very convenient tool for keeping notes/knowledge base for myself or a small group of people.

### Prerequisites

1.  **Docker** and **Docker Compose** installed.
2.  A **No-IP** account.
3.  **Open ports** 80 and 443.

### Setup and Running

1.  Clone repo:
    ```bash
    git clone https://github.com/SemyonDunaev/bookstack_docker.git
    ```

2.  **Configure `.env`**:

    Generate APP_KEY:
    ```bash
    docker run -it --rm --entrypoint /bin/bash lscr.io/linuxserver/bookstack:latest appkey
    ```

    Copy env.example to .env:
    ```bash
    cp env.example .env
    ```

    Ensure `.env` contains the correct data:

    ```env
    # BookStack Application Key
    APP_KEY=APP_KEY including prefix base64

    # No-IP Credentials
    NOIP_USERNAME=
    NOIP_PASSWORD=
    NOIP_DOMAINS=

    # BookStack Database Credentials
    DB_ROOT_PASS=
    DB_USER=bookstack
    DB_PASS=
    DB_DATABASE=bookstackapp

    # Storage
    STORAGE_TYPE=local
    FILE_UPLOAD_SIZE_LIMIT=500 # Mb
    ```

3.  **Start**:
    ```bash
    docker compose -p books up
    ```
    If everything started and works correctly, stop the containers ( Ctrl + C ) and start again:
    ```bash
    docker compose -p books start
    ```

### Access

*   URL: `https://yourhost.ddns.net`
*   **Default Credentials**:
    *   Email: `admin@admin.com`
    *   Password: `password`
    *   *Please change these immediately after logging in!*

---

<a name="russian"></a>
## 🇷🇺 Русский

Docker Compose файл для развертывания [BookStack](https://www.bookstackapp.com/) с использованием Docker Compose, MariaDB, Caddy и No-IP (если нет статического IP).

Bookstack показался мне очень удобным инструментом для ведения заметок/базы знаний для себя или для небольшой группы людей.

### Предварительные требования

1.  **Docker** и **Docker Compose**.
2.  Аккаунт **No-IP**.
3.  **Открытые порты** 80 и 443

### Настройка и запуск

1.  Склонировать репозиторий:  
    ```bash
    git clone https://github.com/SemyonDunaev/bookstack_docker.git
    ```

2.  **Настройте `.env`**:

    Сгенерируйте APP_KEY:
    ```bash
    docker run -it --rm --entrypoint /bin/bash lscr.io/linuxserver/bookstack:latest appkey
    ```

    Cкопируйте env.example в .env:
    ```bash
    cp env.example .env
    ```

    Проверьте, что в файле `.env` указаны верные данные:

    ```env
    # BookStack Application Key
    APP_KEY=APP_KEY including prefix base64

    # No-IP Credentials
    NOIP_USERNAME=
    NOIP_PASSWORD=
    NOIP_DOMAINS=

    # BookStack Database Credentials
    DB_ROOT_PASS=
    DB_USER=bookstack
    DB_PASS=
    DB_DATABASE=bookstackapp

    # Storage
    STORAGE_TYPE=local
    FILE_UPLOAD_SIZE_LIMIT=500 # Mb
    ```

3.  **Запуск**:
    ```bash
    docker compose -p books up
    ```
    Если все нормально запустилось и работает, то остановите контейнеры ( Ctrl + C ) и запустите заново:
    ```bash
    docker compose -p books start
    ``` 

### Доступ

*   Адрес: `https://ваш_домен.ddns.net`
*   **Логин по умолчанию**:
    *   Email: `admin@admin.com`
    *   Пароль: `password`
    *   *Смените их сразу после входа!*
