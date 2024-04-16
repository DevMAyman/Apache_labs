# LAB 1

### 1. Install Apache Web Server

![Screenshot](./Screenshot%20from%202024-04-16%2003-49-50.png)


### 2. Create two simple html pages named “page1.html, page2.html” then use the suitable directive to automatically redirect from localhost/page1.html to localhost/page2.html.

#### 1. Make twos file page1.html and page2.html in /var/www/html/apache2_labs/lab1

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>HELLO FROM PAGE 1</h1>
</body>
</html>
```
_____________________________________________________________________________

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>HELLO FROM PAGE 2</h1>
</body>
</html>
```

#### 2. Edit main  configration file in /etc/apache2/apache2.conf

```bash
<Directory /var/www/html>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```


#### 3. Edit .htaccess wwhich i add it in lab_1 directory 

```
Redirect "/apache2_labs/lab_1/page1.html" "/apache2_labs/lab_1/page2.html"
```


### 3. Create two simple html pages named “page1.html, page2.html” then use the suitable directive to automatically redirect from localhost/page1.html to localhost/page2.html.

#### 1.Add the auth config in .htaccess file

```bash
authType basic
authName "Login first"
authUserFile /apache2_labs/lab_1/.htpass
require valid-user
```

#### 2. Run this command to make myadmin user

```bash
sudo htpasswd -c .htpass myadmin
```
![Screenshot](Screenshot%20from%202024-04-16%2005-27-11.png)


![Screenshot](Screenshot%20from%202024-04-16%2005-34-28.png)

### 4. Apply authentication before downloading PDF files.

```bash
<FilesMatch "\.pdf$">
authType basic
authName "Login first"
authUserFile /var/www/html/apache2_labs/lab_1/.htpass
require valid-user
</FilesMatch>
```
![Screenshot](Screenshot%20from%202024-04-16%2007-09-10.png)

### 5.  Create a directory then allow access to one of your classmates only.

```bash
<Directory /var/www/html >
    Deny from all
    Allow from 192.168.1.4
    Order Deny,Allow
</Directory>
```
![Screenshot](Screenshot%20from%202024-04-16%2007-42-52.png)

### 6. Disable listing the directory content (hint use indexs)

```bash
<Directory  /var/www/html/apache2_labs/lab_1 >
    Options -Indexes
</Directory>
```
![Screenshot](Screenshot%20from%202024-04-16%2007-42-52.png)



### 7. Change the default index page to be default.html instead of index.html (useDirectoryIndex)


```bash
<Dictionary>
    Options -Indexes
    DirectoryIndex page1.html
</Dictionary>
```
![Screenshot](Screenshot%20from%202024-04-16%2008-50-01.png)
