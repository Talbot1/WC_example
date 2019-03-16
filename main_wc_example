import tkinter as tk  # 使用Tkinter前需要先导入
import tkinter.messagebox
import pickle
from wordcloud import WordCloud ,STOPWORDS, ImageColorGenerator
from pylab import matplotlib,mpl
from matplotlib.font_manager import FontManager
import matplotlib.pyplot as plt
import matplotlib
import jieba
from PIL import Image
import numpy as np
from os import path
from imageio import *
 
window = tk.Tk()
 
window.title('WordCloud Demo Application')
 
window.geometry('400x300')  # 这里的乘是小x
 
canvas = tk.Canvas(window, width=400, height=135, bg='green')
image_file = tk.PhotoImage(file='pic.gif')
image = canvas.create_image(200, 0, anchor='n', image=image_file)
canvas.pack(side='top')
tk.Label(window, text='Welcome',font=('Arial', 16)).pack()
 
tk.Label(window, text='Txt_Input    ', font=('Arial', 14)).place(x=10, y=170)
tk.Label(window, text='Picture_Input', font=('Arial', 14)).place(x=10, y=210)
 
var_txt = tk.StringVar()
var_txt.set('1.txt')
entry_txt = tk.Entry(window, textvariable=var_txt, font=('Arial', 14))
entry_txt.place(x=130,y=175)
var_picture = tk.StringVar()
var_picture.set('love.png')
entry_picture = tk.Entry(window, textvariable=var_picture, font=('Arial', 14))
entry_picture.place(x=130,y=215)

d = path.dirname(__file__) if "__file__" in locals() else os.getcwd()#这部没有明白,是从官方文档中抄过来的

def submit():
    
    # 这两行代码就是获取用户输入的txt和picture
    txt = var_txt.get()
    picture = var_picture.get()
    print(txt,picture)
    def wordcloud(d,str1,str2):
        alice_coloring = np.array(Image.open(path.join(d,str2)))#背景图片
        stopwords=set(STOPWORDS)
        stopwords.add("said")
        image_colors = ImageColorGenerator(alice_coloring)

        myfont = (r'tyj.ttf') 
        wc = WordCloud(background_color="white",random_state =2,scale=1,mask=alice_coloring,stopwords=stopwords,collocations=False, font_path=myfont, width=1400, height=1400, margin=2)
        txt = open(path.join(d,str1),encoding='utf-8').read()
        txt_jieba = jieba.cut(txt,cut_all = True)
        txt_finish = " ".join(txt_jieba)

        wc.generate(txt_finish)
        plt.imshow(alice_coloring)
        plt.imshow(wc)
        plt.axis("off")
        plt.show()
        wc.to_file(path.join("名称.jpg"))
    wordcloud(d,txt,picture)
 


btn_login = tk.Button(window, text='Submit', command=submit)
btn_login.place(x=190, y=240)
window.mainloop()
