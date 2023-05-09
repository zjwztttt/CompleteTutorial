### Flask
    from flask import Flask
    
    # 创建Flask应用程序，指定静态文件目录
    app = Flask(__name__, static_folder='templates')
    
    #定义主页路由和函数
    @app.route('/')
    def index():
        return render_template('index.html')
    
    # 定义其他路由
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
    from fastapi import FastAPI, Request  # 导入 FastAPI 框架和 Request 类
    from fastapi.responses import HTMLResponse  # 导入 HTMLResponse 类
    from fastapi.templating import Jinja2Templates  # 导入 Jinja2Templates 类
    import uvicorn  # 导入 uvicorn 模块

    app = FastAPI()  # 创建 FastAPI 实例
    templates = Jinja2Templates(directory="templates")  # 创建 Jinja2Templates 实例

    @app.get("/", response_class=HTMLResponse)  # 定义路由和请求方法
    async def read_item(request: Request):  # 定义异步函数，接收 Request 对象作为参数
        # 返回 HTML 模板
        return templates.TemplateResponse("index.html", {"request": request})
    
    if __name__ == "__main__":
        # 启动应用程序
        uvicorn.run(
            app,
            host='192.168.31.28',
            port=8080,
        )
### Hypercorn(基于asyncio的ASGI服务器)
### Gunicorn(WSGI服务器)
### Daphne(基于Twisted的ASGI服务器)
