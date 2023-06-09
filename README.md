<a href="https://ngrok.com/">
<img alt="Socket.IO" src="https://ngrok.com/static/img/ngrok-white.svg" 
  height="150"
/></a>

Try to ngrok on docker.

# Usage

## Login or signup in ngrok site, And copy your authtoken.

- Login or signup from below ngrok site.  
  [https://dashboard.ngrok.com/](https://dashboard.ngrok.com/)

- Copy your authtoken from below.  
  [https://dashboard.ngrok.com/get-started/your-authtoken](https://dashboard.ngrok.com/get-started/your-authtoken)

## 1. Create `.env` file.

```
$ cp .env.example .env
```

## 2. Write you want to setting into `.env` file.

```
# example
NGROK_TARGET=3000
```

### ※ If you need Basic Autentication

In `.env` file,  
write to your authcode into `NGROK_AUTH`  
and set to info of Basic Autentication into `NGROK_AUTH`, `NGROK_PASSWORD`,  
and uncomment row of below in `compose.yml`.

```
    # Basic 認証
    # NGROK_USERNAME: ${NGROK_USERNAME}
    # NGROK_PASSWORD: ${NGROK_PASSWORD}
    # NGROK_AUTH: ${NGROK_AUTH}
```

## 3. Build ngrok container.

```
$ make up
```

## 4. Register your authcode in ngrok container only once.(Only if you haven't never register yet.)

- Come in ngrok container.

```
$ make exec-ngrok
```

- Register your authcode.

```
# in ngrok container
/ $ ngrok authtoken <your authcode>
```

## 5. Restart ngrok container

```
$ make down up
```

## 6. Confirm your ngrok status.

[http://localhost:<NGROK_PORT>/inspect/http](http://localhost:<NGROK_PORT>/inspect/http)

※ `NGROK_PORT` is your setting.
