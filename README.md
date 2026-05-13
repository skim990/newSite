from wsgiref.util import application_uri

from flask import Flask, render_template
from flask_sqlalchemy import SQLAlchemy
app =  Flask(__name__)

app.config ['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///newflask.db'
db= SQLAlchemy (app)

class Post (db.Model):
    id= db.Column (db.Integer, primary_key=True)
    title = db.Column (db.String(300), nullable=False)
    text = db.Column (db.Text, nullable=False)



@app.route('/index')
@app.route('/')
def index():
    return render_template('index.html')

@app.route('/about')
@app.route('/о себе')
def about():
    return render_template('about.html')

@app.route('/пятки')
def пятки():
    return '<h1> пятки<3 </h1>'

@app.route('/product')
@app.route('/Продукт')
@app.route('/Игры')
@app.route('/товар')
def product():
    return render_template('product.html')

@app.route('/basket')
@app.route('/Корзина')
@app.route('/Покупки')
@app.route('/Корзинка с какашками')
def basket():
    return render_template('basket.html')

if __name__=='__main__':
    app.run(debug=True)
