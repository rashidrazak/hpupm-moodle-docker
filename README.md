# HPUPM Moodle Docker

## Preparation

### 1. Clone Repository

Clone this repository. Preferably in `/root`. Anywhere is fine, though.

```bash
cd /root
git clone https://github.com/rashidrazak/hpupm-moodle-docker.git
```

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

### 2. Start the Stack

To run the Moodle stack, use the following command:

```bash
docker-compose up -d
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
