<a href="https://ngrok.com/">
<img alt="Socket.IO" src="https://ngrok.com/static/img/ngrok-white.svg" 
  height="150"
/></a>

Trying to Ngrok on docker.

# Usage

## 1. Create `.env` file.

```
$ cp .env.example .env
```

## 2. Write you want to setting into `.env` file.

```
# example
NGROK_TARGET=3000
```

## 3. Build Ngrok container.

```
$ make up
```

## 4. Login Ngrok site, And copy your authtoken.

- Login from below.  
  [https://dashboard.ngrok.com/login](https://dashboard.ngrok.com/get-started/setup)

- Copy your authtoken from below.  
  [https://dashboard.ngrok.com/get-started/your-authtoken](https://dashboard.ngrok.com/get-started/your-authtoken)

## 5. Register your authcode in Ngrok container only once.

- Come in Ngrok container.

```
$ make exec-ngrok
```

- Register your authcode.

```
# in Ngrok container
/ $ ngrok authtoken <your authcode>
```

## 6. Restart Ngrok container

```
$ make down up
```

## 7. Confirm your Ngrok status.

[http://localhost:<NGROK_PORT>/inspect/http](http://localhost:<NGROK_PORT>/inspect/http)

※ NGROK_PORT is your setting.

## If you need Basic Autentication

In `.env` file,  
write to your authcode into NGROK_AUTH  
and set to info of Basic Autentication into NGROK_AUTH, NGROK_PASSWORD,  
and uncomment row of below in `compose.yml`.

```
    # Basic 認証
    # NGROK_USERNAME: ${NGROK_USERNAME}
    # NGROK_PASSWORD: ${NGROK_PASSWORD}
    # NGROK_AUTH: ${NGROK_AUTH}
```

※ Don't forget to restart ngrok container.
