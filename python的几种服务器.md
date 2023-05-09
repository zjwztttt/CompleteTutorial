### Flask
    from flask import Flask, request, jsonify, render_template
    # 创建Flask应用程序
    app = Flask(__name__, static_folder='templates')
    #定义主页路由和函数
    @app.route('/', methods=['GET'])
    def index():
        return render_template('index.html')
    
    if __name__ == '__main__':
        app.run(
            host='192.168.31.28',
            port=8080,
            debug=True,
            load_dotenv=False,#False OR True
        )
#### Fastapi + uvicorn
    from fastapi import FastAPI
    import uvicorn
    app = FastAPI()
    
    if __name__ == "__main__":
        uvicorn.run(
            app,
            host=web_host,
            port=web_port,
            #config=config
        )
