### Assignment 2: What are nginx header security and its uses. And also implement in the test.conf file.

# Security headers in nginx:

Nginx Seacurity headers are the extra headers that are added by nginx into the incoming web requests before the requests are passed
to the running application servers. HTTP security headers are very important part of website security as it protect you against different types of attacks including, XSS, SQL injection, clickjacking, etc

Some of tthe common nginx security headers are :

# 1. HTTP Strict Transport Security (HSTS):

    This header required the client to use only HTTPS connections. Any non https request are blocked by the nginx server.
    It can be added in nginx as:
    ```
    add_header Strict-Transport-Security 'max-age=31536000; includeSubDomains; preload';

    ```

# 2. X-XSS-Protection(Cross-Stie Scription protection):

    X-Xss proctection header is to protect our site from cross site scription acttacks. Ite is already enabled by default by the browser.
    It offers differnt level of protection depending on the value and mode of the header
    ```
    X-XSS-Protection: 0

    X-XSS-Protection: 1

    X-XSS-Protection: 1; mode=block

    X-XSS-Protection: 1; report=
    ```

    It is added in nginx as:
    ```
    add_header X-XSS-Protection "1; mode=block";
    ```

# 3. Content Security Policy (CSP)

    It is an imporved version of x-xss protectin header. It instructs browser to load only allowed contesnt onthe website.
    However it all browsers don't support it completely.
    Ite is used in nginx as :

    ```
    add_header Content-Security-Policy "default-src 'self'; font-src *;img-src * data:; script-src *; style-src *";

    ```

# 4.X-Frame-Options(Website ifrmae protection)

    It is used to prevent clickjacking attack by disableing iframes in the site. It instructs the browse to to embod our website in other iframes.
    It can be configured as these options:
    ```

    DENY : This will disables iframe features completely.
    SAMEORIGIN : iframe can be used only by someone on the same origin.
    ALLOW-FROM : This will allows pages to be put in iframes only from specific URLs.

    ```

    ```
    add_header X-Frame-Options "SAMEORIGIN";
    ```

# 5. X-Content-Type-Options(Preventing content type sniffing)

     It instructs the browser to follow the MIME types indicate in the header.

    ```
    add_header X-Content-Type-Options nosniff;
    ```

Nginx security headers can be added in the server block of nginx configuration file as :

```

server {

        listen 80;


        root /var/www/localhost/html;

        index index.html index.htm index.nginx-debian.html;

        server_name localhost;

        location / {

                try_files $uri $uri/ =404;

        }

        access_log /var/log/nginx/test.log;

        error_log /var/log/nginx/test-error.log;

        # Some security headers.

        add_header Referrer-Policy "strict-origin";

        add_header X-XSS-Protection "1; mode=block";

        add_header X-Frame-Options "SAMEORIGIN";

        add_header X-Content-Type-Options nosniff;


}


```

![In conf file](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/2/screenshot/nginx-sercurity-headers.png)

Security headers visibility in the browser:

![Headers in website](https://github.com/LF-DevOps-Intern/4_2_nginx-krishna-surpriso1997/blob/master/2/screenshot/security-headers.png)
