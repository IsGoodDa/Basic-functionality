以下是基础功能模块的 Python 代码示例：

from flask import Flask, render_template, request, redirect, url_for, flash

from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)

app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///users.db'

app.config['SECRET_KEY'] = 'your_secret_key'

db = SQLAlchemy(app)

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(50), unique=True, nullable=False)
    password = db.Column(db.String(100), nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)
    role = db.Column(db.String(20), nullable=False)

    def __repr__(self):
    
        return '<User %r>' % self.username

@app.route('/register', methods=['GET', 'POST'])

def register():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        email = request.form['email']
        role = request.form['role']

        user = User(username=username, password=password, email=email, role=role)
        db.session.add(user)
        db.session.commit()

        flash('注册成功，请登录！')
        return redirect(url_for('login'))

    return render_template('register.html')

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']

        user = User.query.filter_by(username=username).first()

        if user and user.password == password:
            return redirect(url_for('profile'))

        flash('用户名或密码错误，请重新登录！')

    return render_template('login.html')

@app.route('/profile', methods=['GET', 'POST'])
def profile():
    if request.method == 'POST':
        user = User.query.filter_by(id=1).first()
        user.username = request.form['username']
        user.password = request.form['password']
        user.email = request.form['email']
        db.session.commit()

        flash('修改成功！')
        return redirect(url_for('profile'))

    user = User.query.filter_by(id=1).first()
    return render_template('profile.html', user=user)

if __name__ == '__main__':
    app.run(debug=True)
在这个示例中，我们使用 Flask 框架和 SQLAlchemy 作为 ORM 工具来搭建基础功能模块。其中，我们定义了一个 User 数据库模型来存储用户信息，包括用户名、密码、邮箱和角色。我们还定义了注册、登录和个人信息查看和修改等路由函数，并对其进行了相应的处理。最后，我们通过 app.run() 函数来启动应用程序并监听本地的 HTTP 请求。
