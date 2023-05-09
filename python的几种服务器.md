### Flask
    from flask import Flask
    
    # 创建Flask应用程序，指定静态文件目录
    app = Flask(__name__, static_folder='templates')
    
    #定义主页路由和函数
    @app.route('/')
    def index():
        return render_template('index.html')
    
    # 定义其他路由，请求方式为`POST`,也可以改成`GET`
    @app.route('/save_url', methods=['POST'])
    def save_url():
        return "Hello,world!"
    
    if __name__ == '__main__':
        app.run(
            host='192.168.31.28',
            port=8080,
            debug=True,
            load_dotenv=False,#False OR True
        )
#### Fastapi + Uvicorn(基于sans-io hyper、h11、h2和wsproto库的ASGI服务器)
    from fastapi import FastAPI, Request
    from fastapi.responses import HTMLResponse
    from fastapi.templating import Jinja2Templates
    import uvicorn

    # 创建 FastAPI 实例
    app = FastAPI()
    # 创建 Jinja2Templates 实例
    templates = Jinja2Templates(directory="templates")

    # 定义路由和请求方法
    # 定义异步函数，接收 Request 对象作为参数
    @app.get("/", response_class=HTMLResponse)
    async def read_item(request: Request):
        # 返回 HTML 模板
        return templates.TemplateResponse("index.html", {"request": request})
    
    # 定义其他路由，请求方式`post`，也可以改成`get`
    @app.post('/other')
    async def chatbot(request: Request):
        return "Hello,world!"
    
    if __name__ == "__main__":
        # 启动应用程序
        uvicorn.run(
            app,
            host='192.168.31.28',
            port=8080,
        )
### Hypercorn(基于asyncio的ASGI服务器)
    from fastapi import FastAPI, Request
    from fastapi.responses import HTMLResponse
    from fastapi.templating import Jinja2Templates
    from hypercorn.config import Config  # 导入 Hypercorn 配置类
    from hypercorn.asyncio import serve  # 导入 Hypercorn serve 函数
    import asyncio

    # 创建 FastAPI 实例
    app = FastAPI()
    # 创建 Jinja2Templates 实例
    templates = Jinja2Templates(directory="templates")

    # 定义路由和请求方法
    # 定义异步函数，接收 Request 对象作为参数
    @app.get("/", response_class=HTMLResponse)
    async def read_item(request: Request):
        # 返回 HTML 模板
        return templates.TemplateResponse("index.html", {"request": request})

    if __name__ == "__main__":
        # 创建 Hypercorn 配置实例
        config = Config()
        # 注意证书路径
        config.certfile = "/etc/mycert/cert.pem"
        config.keyfile = "/path/mycert/key.pem"
        # 设置绑定地址和端口号
        config.bind = ["0.0.0.0:5080"]
        # 启用HTTP2
        config.protocol = "h2"
        # 启动应用程序
        asyncio.run(serve(app, config))
### Gunicorn(WSGI服务器)
    gunicorn -w 4 -b 127.0.0.1:5000 app_name:app
### Daphne(基于Twisted的ASGI服务器)
