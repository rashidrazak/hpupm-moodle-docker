# HPUPM Moodle Docker

## Preparation

### 1. Clone Repository

Clone this repository. Preferably in `/root`. Anywhere is fine, though.

```bash
cd /root
git clone https://github.com/rashidrazak/hpupm-moodle-docker.git
```

### 2. Prepare Binded Directory

Make sure these directories exist. If not, simply run `mkdir` to create them.

- public_html
- moodledata
- bht_moodledata
- postgresql_data

### 2. Download Moodle

Moodle need to be put inside `public_html` directory.

```bash
cd /root/hpupm-moodle-docker/public_html
git clone -b MOODLE_310_STABLE git://git.moodle.org/moodle.git .
```

### 3. Create Moodle Data Directory

```bash
cd /root/hpupm-moodle-docker
mkdir moodledata
```

## Starting the Stack

### 1. Populate .env File

Copy the `.env-sample` file and rename the new file as `.env`. Then, populate the `.env` file with correct values.
Variable `POSTGRES_PASSWORD` is compulsory. `POSTGRES_USER` and `POSTGRES_DB` will have the value of `postgres` if not specified.

### 2. Start the Stack

To run the Moodle stack, use the following command:

```bash
docker-compose up -d
```

### 3. Install Moodle

To install Moodle via web installer, visit `http://localhost:8000` and follow the wizard.

`config.php` additional setup:

```php
$CFG->behat_dataroot = '/app/bht_moodledata';
$CFG->behat_prefix = 'bht_';
$CFG->behat_wwwroot = 'http://127.0.0.1:8000';
```

## Stopping the Stack

```bash
docker-compose down
```

## [DANGER!!!] Reset Everything

If you need to reset everything, run this.

```bash
docker-compose down --rmi all
```

## References

List of Docker Hub repositories used:

- [Apache](https://hub.docker.com/_/httpd)
- [PHP](https://hub.docker.com/_/php)
- [PostgreSQL](https://hub.docker.com/_/postgres)
- [Adminer](https://hub.docker.com/_/adminer)
