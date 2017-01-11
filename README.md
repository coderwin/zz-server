# zz-server

>Mock a REST API fly(前后端分离中快速mock rest api)

>和json-server的使用方法一样，但是json-server不支持https接口的mock

## use

* install

```
npm install -g zz-server
```

* gen key
    
    > path是你要把证书文件声称到的文件夹
    - 生成私钥key文件
    
    ```
    openssl genrsa 1024 > /path/private.pem
    ```

    - 通过私钥文件生成CSR证书签名
    
    ```
    openssl req -new -key /path/private.pem -out csr.pem
    ```
    - 通过私钥文件和CSR证书签名生成证书文件
    
    ```
    openssl x509 -req -days 365 -in csr.pem -signkey /path/private.pem -out /path/file.crt
    ```
    
* run server
    
    ```
    zz-server --ENTRY db.js --KEYPATH key --PORT 18088 --SSLPORT 18089
    ```
    
    - Usage: zz-server [options]
    - Options:
    
        - -h, --help             output usage information
        - -v, --version          output the version number
        - -e, --ENTRY [value]    设置模拟的接口入口文件path|默认为命令行运行目录
        - -k, --KEYPATH [value]  设置https证书path|默认为命令行运行目录
        - -p, --PORT [value]     设置http接口监听端口|默认为18080
        - -s, --SSLPORT [value]  设置https接口监听端口|默认为18081
        
* you can look
    
```
key entry: /Users/a58/Documents/work/zz/zz-cz/ZZMuying/api/key
db entry: /Users/a58/Documents/work/zz/zz-cz/ZZMuying/api/db.js
HTTP Server is running on: http://10.252.164.89:18080
HTTPS Server is running on: https://10.252.164.89:18081
``` 

* THX
    - express
