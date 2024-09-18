
# WordPress Development Environment with Docker

## Overview

This guide helps you set up a basic WordPress development environment using Docker for faster development. It includes instructions on handling MySQL in `.gitignore` and managing file permissions.

## Ignore MySQL Folder in Git

1. Create a `.gitignore` file:
   ```bash
   touch .gitignore
   ```

2. Open the `.gitignore` file in nano:
   ```bash
   nano .gitignore
   ```

3. Add the following line to ignore the MySQL folder:
   ```plaintext
   /mysql/
   ```

4. Check if the `mysql` folder is being ignored:
   ```bash
   git check-ignore -v mysql/*
   ```

5. If `mysql` was already added to Git, remove it from cache:
   ```bash
   git rm -r --cached mysql/
   ```

6. Add the `.gitignore` changes to Git:
   ```bash
   git add .gitignore
   ```

7. Commit the changes:
   ```bash
   git commit -m "Add mysql folder to .gitignore"
   ```

8. Check the Git status to ensure everything is correct:
   ```bash
   git status
   ```

## Managing File Permissions

### With `www-data` as User in Docker-Compose

1. Enter the container's bash:
   ```bash
   docker exec -it container_name /bin/bash
   ```

2. Set the correct permissions for the `wp-content` folder:
   ```bash
   chmod -R 755 /var/www/html/wp-content
   ```

3. Set `www-data` as the owner of the `wp-content` folder:
   ```bash
   chown -R www-data:www-data /var/www/html/wp-content
   ```

### If Root or Another User (e.g., `smadmin`)

1. Adjust permissions using your system user (in this case `smadmin`):
   ```bash
   sudo chmod 755 /home/smadmin/dockers/wpdocker/wp-content
   ```

2. Change ownership of the `wp-content` folder to `smadmin`:
   ```bash
   sudo chown -R smadmin:smadmin /home/smadmin/dockers/wpdocker/wp-content
   ```

---

Follow these steps to ensure a smooth setup and development process for your WordPress environment.
