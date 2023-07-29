# CODEMATE项目组

本项目主要进行与爬虫相关的具体实现以及对于得到的数据通过机器学习的方法进行筛选。

## CSDN

我们首先自行学习了解了网页的构成以及网页请求响应过程，然后我们学习了有关爬虫的相关内容，如requests库，Xpath以及构建DOM Tree等。

随后我们开始爬取CSDN上的有关内容（具体内容为CSDN问答中已采纳的部分），我要爬取的内容是数据结构有关，具体如下：
<details>

    "数据的逻辑结构",
    "时间复杂度的概念",
    "算法运算量的计算",
    "渐进表示法",
    "时间复杂度的计算",
    "面向对象的概念",
    "用面向对象的思想讨论数据结构",
    "面向对象方法中数据结构的描述与实现",
    "线性表的基本概念",
    "顺序表的存储实现",
    "基本运算在顺序表上的实现",
    "顺序实现的算法分析",
    "单链表",
    "双链表",
    "循环链表",
    "线性表的抽象类",
    "顺序表类的实现",
    "双链表类的实现",
    "容器和迭代器的概念",
    "vector 类和 list 类",
    "vector 类和 list 类的使用",
    "双端队列-deque",
    "线性表的应用：文本编辑系统",
    "栈的基本概念",
    "栈的顺序实现",
    "栈的链接实现",
    "栈的抽象类",
    "顺序栈类的实现",
    "链接栈类的实现",
    "STL 中的栈",
    "递归消除",
    "括号配对",
    "简单的计算器",
    "队列的概念",
    "队头位置固定的顺序实现",
    "队头位置不固定的顺序实现",
    "循环队列",
    "队列的链接实现",
    "队列的抽象类",
    "循环队列类的实现",
    "链接队列类的实现",
    "STL 中的队列",
    "队列的应用: 排队系统的模拟",
    "树的定义",
    "树的基本术语",
    "树的基本运算",
    "二叉树的基本概念",
    "二叉树的主要性质",
    "二叉树的基本运算和二叉树的遍历",
    "二叉树的顺序实现",
    "二叉树的链接实现",
    "二叉树类的实现",
    "二叉树遍历的非递归实现",
    "二叉树的应用：计算表达式",
    "哈夫曼树和哈夫曼编码",
    "树和森林",
    "树的存储实现",
    "树的遍历",
    "树、林与二叉树的关系",
    "基本的优先级队列",
    "二叉堆的结构性",
    "二叉堆的有序性",
    "基于二叉堆的优先级队列的实现",
    "D堆",
    "左堆",
    "斜堆",
    "贝努利队列",
    "STL 中的优先级队列",
    "多服务台排队系统的模拟",
    "集合的基本概念",
    "查找的基本概念",
    "静态表查找",
    "无序表的查找",
    "顺序查找",
    "顺序查找的时间复杂度分析",
    "二分查找",
    "插值查找",
    "分块查找",
    "静态查找表的实现",
    "STL 中的静态表",
    "二叉查找树的定义",
    "二叉查找树的操作",
    "二叉查找树的性能",
    "二叉查找树类的实现",
    "AVL 树的定义",
    "AVL 树的插入操作",
    "AVL 树的删除操作",
    "AVL 树类的实现",
    "红黑树的定义",
    "红黑树的插入操作",
    "红黑树的删除操作",
    "红黑树类的实现",
    "AA 树的定义",
    "AA 树的插入操作",
    "AA 树的删除操作",
    "AA 树类的实现",
    "伸展树的定义",
    "伸展操作的实现",
    "B 树",
    "B+ 树",
    "set",
    "map",
    "散列表",
    "散列函数",
    "线性探测法",
    "二次探测法",
    "再散列法",
    "开散列表",
    "散列表类的抽象类",
    "闭散列表的实现",
    "开散列表的实现",
    "散列表类的应用",
    "插入排序",
    "直接插入排序",
    "二分插入排序",
    "希尔排序",
    "希尔排序的性能",
    "直接选择排序",
    "堆排序",
    "冒泡排序",
    "快速排序",
    "归并排序",
    "外排序的基本过程",
    "预处理阶段",
    "归并阶段",
    "等价关系与等价类",
    "不相交集",
    "不相交集的存储实现",
    "不相交集的运算实现",
    "改进的union算法",
    "改进的find算法",
    "不相交集类的实现",
    "生成迷宫",
    "最近的共同祖先问题",
    "图的定义",
    "图的基本术语",
    "图的基本运算",
    "邻接矩阵表示法",
    "邻接表表示法",
    "深度优先搜索 DFS",
    "广度优先搜索 BFS",
    "无向图的连通性",
    "欧拉回路",
    "有向图的连通性",
    "拓扑排序",
    "生成树和最小生成树",
    "Kruskal算法",
    "Prim算法",
    "最小生成树算法的正确性",
    "非加权图的最短路径",
    "加权图的最短路径",
    "带有负权值的图",
    "无环图",
    "所有顶点对的最短路径"
```
```
</details>    
<br>







以下是相关代码




<details>
  <summary>点击展开/收起代码</summary>
  
  ```python
import requests
import json
import jsonlines
import asyncio
import aiohttp
import time
from lxml import etree
# headers={'User-Agent':'Your User-Agent'}

content = [
    "数据的逻辑结构",
    "时间复杂度的概念",
    "算法运算量的计算",
    "渐进表示法",
    "时间复杂度的计算",
    "面向对象的概念",
    "用面向对象的思想讨论数据结构",
    "面向对象方法中数据结构的描述与实现",
    "线性表的基本概念",
    "顺序表的存储实现",
    "基本运算在顺序表上的实现",
    "顺序实现的算法分析",
    "单链表",
    "双链表",
    "循环链表",
    "线性表的抽象类",
    "顺序表类的实现",
    "双链表类的实现",
    "容器和迭代器的概念",
    "vector 类和 list 类",
    "vector 类和 list 类的使用",
    "双端队列-deque",
    "线性表的应用：文本编辑系统",
    "栈的基本概念",
    "栈的顺序实现",
    "栈的链接实现",
    "栈的抽象类",
    "顺序栈类的实现",
    "链接栈类的实现",
    "STL 中的栈",
    "递归消除",
    "括号配对",
    "简单的计算器",
    "队列的概念",
    "队头位置固定的顺序实现",
    "队头位置不固定的顺序实现",
    "循环队列",
    "队列的链接实现",
    "队列的抽象类",
    "循环队列类的实现",
    "链接队列类的实现",
    "STL 中的队列",
    "队列的应用: 排队系统的模拟",
    "树的定义",
    "树的基本术语",
    "树的基本运算",
    "二叉树的基本概念",
    "二叉树的主要性质",
    "二叉树的基本运算和二叉树的遍历",
    "二叉树的顺序实现",
    "二叉树的链接实现",
    "二叉树类的实现",
    "二叉树遍历的非递归实现",
    "二叉树的应用：计算表达式",
    "哈夫曼树和哈夫曼编码",
    "树和森林",
    "树的存储实现",
    "树的遍历",
    "树、林与二叉树的关系",
    "基本的优先级队列",
    "二叉堆的结构性",
    "二叉堆的有序性",
    "基于二叉堆的优先级队列的实现",
    "D堆",
    "左堆",
    "斜堆",
    "贝努利队列",
    "STL 中的优先级队列",
    "多服务台排队系统的模拟",
    "集合的基本概念",
    "查找的基本概念",
    "静态表查找",
    "无序表的查找",
    "顺序查找",
    "顺序查找的时间复杂度分析",
    "二分查找",
    "插值查找",
    "分块查找",
    "静态查找表的实现",
    "STL 中的静态表",
    "二叉查找树的定义",
    "二叉查找树的操作",
    "二叉查找树的性能",
    "二叉查找树类的实现",
    "AVL 树的定义",
    "AVL 树的插入操作",
    "AVL 树的删除操作",
    "AVL 树类的实现",
    "红黑树的定义",
    "红黑树的插入操作",
    "红黑树的删除操作",
    "红黑树类的实现",
    "AA 树的定义",
    "AA 树的插入操作",
    "AA 树的删除操作",
    "AA 树类的实现",
    "伸展树的定义",
    "伸展操作的实现",
    "B 树",
    "B+ 树",
    "set",
    "map",
    "散列表",
    "散列函数",
    "线性探测法",
    "二次探测法",
    "再散列法",
    "开散列表",
    "散列表类的抽象类",
    "闭散列表的实现",
    "开散列表的实现",
    "散列表类的应用",
    "插入排序",
    "直接插入排序",
    "二分插入排序",
    "希尔排序",
    "希尔排序的性能",
    "直接选择排序",
    "堆排序",
    "冒泡排序",
    "快速排序",
    "归并排序",
    "外排序的基本过程",
    "预处理阶段",
    "归并阶段",
    "等价关系与等价类",
    "不相交集",
    "不相交集的存储实现",
    "不相交集的运算实现",
    "改进的union算法",
    "改进的find算法",
    "不相交集类的实现",
    "生成迷宫",
    "最近的共同祖先问题",
    "图的定义",
    "图的基本术语",
    "图的基本运算",
    "邻接矩阵表示法",
    "邻接表表示法",
    "深度优先搜索 DFS",
    "广度优先搜索 BFS",
    "无向图的连通性",
    "欧拉回路",
    "有向图的连通性",
    "拓扑排序",
    "生成树和最小生成树",
    "Kruskal算法",
    "Prim算法",
    "最小生成树算法的正确性",
    "非加权图的最短路径",
    "加权图的最短路径",
    "带有负权值的图",
    "无环图",
    "所有顶点对的最短路径"
]

async def get(url):
    session = aiohttp.ClientSession()
    response = await session.get(url)
    await response.text()
    await session.close()
    return response

async def request(s):
    url = 'https://so.csdn.net/api/v3/search?q={}&t=ask&p={}&s=0&tm=0&lv=-1&ft=0&l=&u=&ct=-1&pnt=-1&ry=-1&ss=-1&dct=-1&vco=-1&cc=-1&sc=-1&akt=-1&art=-1&ca=1&prs=&pre=&ecc=-1&ebc=-1&ia=1&dId=&cl=-1&scl=-1&tcl=-1&platform=pc'
    for i in range(31):
        response = await get(url.format(s,i))
        result_dic=await response.json()
        if 'result_vos' in result_dic:
            QA_list=result_dic["result_vos"]
        else:
            continue
        if not QA_list:
            print("empty shit")
            continue
        print ("%d Begin" % i) 
        print ("Loading...")
            
            # with open('example.txt', 'w',encoding="utf-8") as f:
            #     f.write(str(QA_list))
            
        for QA in QA_list:
            detail_url=QA["url"]
            response=await get(detail_url)
            tree=etree.HTML(await response.text())
            title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
                # //*[@id="content-7775821"]/div
                # //*[@id="content-7775821"]/div/h6
                # /html/body/div[3]/div/main/div/div[1]/div[1]/section[5]/div/div[1]/div/div/div/div/h6
            question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
            stringque = title+":"
            for mem in question:
                stringque+=mem
            tmppair={"Answer":QA["answer"],"Knowledge_Point": s,"Question":stringque,"Tag":"数据结构"}
                # print (tmppair)
            sstmp='{}.jsonl'
            print(s)
            with jsonlines.open(sstmp.format(s), 'a') as Writer:
                Writer.write(tmppair)
        print("%d End" % i)    
tasks=[]
for newelement in content:
    tasks.append(asyncio.ensure_future(request(newelement)))
loop = asyncio.get_event_loop()
loop.run_until_complete(asyncio.wait(tasks))








# for element in content:
#     s='https://so.csdn.net/api/v3/search?q={}&t=ask&p={}&s=0&tm=0&lv=-1&ft=0&l=&u=&ct=-1&pnt=-1&ry=-1&ss=-1&dct=-1&vco=-1&cc=-1&sc=-1&akt=-1&art=-1&ca=1&prs=&pre=&ecc=-1&ebc=-1&ia=1&dId=&cl=-1&scl=-1&tcl=-1&platform=pc'

#     response1=requests.get(url=s.format(element,1))
#     result_dic1=response1.json()
#     # QA_list1=result_dic1["result_vos"]
#     totalnum=result_dic1["total_page"]
#     print (totalnum)
#     j=1
#     myQApair={}
#     for i in range(1,(int)(totalnum+1)):
        
#         response=requests.get(url=s.format(element,i))
#         result_dic=response.json()
#         if 'result_vos' in result_dic:
#             QA_list=result_dic["result_vos"]
#         else:
#             continue
        
#         if not QA_list:
#             print("empty shit")
#             continue
#         print ("%d Begin" % i) 
#         print ("Loading...")
        
#         # with open('example.txt', 'w',encoding="utf-8") as f:
#         #     f.write(str(QA_list))
        
#         for QA in QA_list:
#             detail_url=QA["url"]
            
#             response=requests.get(url=detail_url)
#             tree=etree.HTML(response.text)
#             title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
#             # //*[@id="content-7775821"]/div
#             # //*[@id="content-7775821"]/div/h6
#             # /html/body/div[3]/div/main/div/div[1]/div[1]/section[5]/div/div[1]/div/div/div/div/h6
#             question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
#             stringque = ""
#             for mem in question:
#                 stringque+=mem
#             tmppair={"Answer":QA["answer"],"Knowledge_Point": element,"Question":stringque,"Tag":"数据结构"}
#             # print (tmppair)
#             myQApair[j]=tmppair
#             j+=1
#             print(j)
#             sstmp='{}.jsonl'
#             print(element)
#             with jsonlines.open(sstmp.format(element), 'a') as Writer:
#                 Writer.write(tmppair)
#         print("%d End" % i)
#     print(element)
#     print("END!!!!!!!!!")
#     print("@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@--------------------------@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@")




  ```
</details>

<br>





大概的执行过程如下：首先进入 CSDN 搜索我们需要的关键字（已采纳的）。我们点开控制台，其中有一个`search? q`开头的包。我们发现这个就是我们所需要的，且是以`dict`形式存在。里面的`resultvos` 中有我们想要得到的东西，然后我们使用`xpath `相关的知识就能可以获取对应的问题和答案了。

这份代码中被注释掉的部分是一开始的做法，然后未被注释掉的是通过但是通过 `asyncio` 库并行爬虫以提高效率（真的快了很多，但是有个缺陷就是爬取的数据会比普通方法略微少一点，少接近20％）。




下面是通过`Selenium`来获取 [https://ask.csdn.net/channel/1005?rewardType&stateType=0&sortBy=1&quick=6&essenceType=1&tagName=essence](https://ask.csdn.net/channel/1005?rewardType&stateType=0&sortBy=1&quick=6&essenceType=1&tagName=essence) 所有具体问答。这中间模拟了鼠标滚轮下滑来获取所有链接。（这是因为页面是实时渲染的）。

<details>
  <summary>点击展开/收起代码</summary>
  
  ```python

from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from bs4 import BeautifulSoup
import time
import requests
import json
import jsonlines
from lxml import etree
from opencc import OpenCC
options = webdriver.ChromeOptions()
options.set_capability("unhandledPromptBehavior", "ignore")
driver = webdriver.Edge(options=options)
url = "https://ask.csdn.net/channel/1005?rewardType&stateType=0&sortBy=1&quick=6&essenceType=1&tagName=essence"
driver.get(url)
set1={1,2,3}
set1.clear
def scroll_down():
    for i in range(1,26):
        driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
        time.sleep(1)  # 等待页面加载新内容
        driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
        time.sleep(1)  # 等待页面加载新内容
        driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
        time.sleep(1)  # 等待页面加载新内容
        driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
        time.sleep(1)  # 等待页面加载新内容
        driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
scroll_down()  # 模拟向下滑动页面加载内容

html = driver.page_source
tree=etree.HTML(html)
title=tree.xpath('//div[@class="title-box"]//a/@href')
print (title)
print(len(title))
for ele in title:
    set1.add(ele)
print ("setchangdu",len(set1))

for ele in title:
    driver.get(ele)
    # response=requests.get(url=url)
    # tree=etree.HTML(response.text)

    html = driver.page_source
    tree=etree.HTML(html)
    #  title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
    #  question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
    # title=tree.xpath('//div[@id="mw-content-text"]//text()')

    question=tree.xpath('//section[@class="title-box"]//text()')
    print(question)
    que=''
    for elel in question:
        que+=elel
    question2=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
    print(question2)
    que2=''
    for elel in question2:
        que2+=elel
    print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~'~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")
    # class="show_answer_content_box md_content"
    ans=tree.xpath('//div[@class="show_answer_content_box md_content"]//div[@class="answer-content-item"]//text()')
    print(ans)
    an2=''
    for elel in ans:
        an2+=elel
    print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")
    point=tree.xpath('//ul[@class="taglist"]//text()')
    print(point)
    pointlist=''
    for element in point:
        if element==' ':
            continue
        pointlist+=(element+' ')
    qapair={"Answer":an2,"Knowledge_Point": pointlist,"Tag":'数据结构',"Question":que+':'+que2}
    with jsonlines.open('数据结构与算法.jsonl','a') as fp:
        fp.write(qapair)
    # time.sleep(0.5)
    with jsonlines.open('网页.jsonl','a') as fp:
        fp.write(ele)
        fp.write(qapair)













driver.quit()

  ```
</details>
<br>

一开始我犯了个错误，我用`response`来获取，但是获取的永远都是没下拉过的界面（也即只有30条）,后面我才知道得用`drive`来获取实时渲染的东西。


注意：模拟浏览器进入页面后，页面并非立刻加载完成，所以需要使用 `time.sleep()` 等待一段时间，否则会无法获取信息。

### WIKI

这和CSDN其实差不多，只不过我们用了所谓找“编辑”的方法来获取具体内容（这是因为通过判断有无“[编辑]”）即可得知这是否是新的一部分。

下面是普通代码。

<br>
<details>
  <summary>点击展开/收起代码</summary>
  
  ```python

import requests
import json
import jsonlines
from lxml import etree
from opencc import OpenCC
# headers={'User-Agent':'Your User-Agent'}
converter=OpenCC('t2s')
content = [
    # "栈",
    # # "数据的逻辑结构",
    # "时间复杂度",
    # "算法",
    # # "渐进表示法",
    # # "时间复杂度的计算",
    # "面向对象的程序设计",
    # # "用面向对象的思想讨论数据结构",
    # # "面向对象方法中数据结构的描述与实现",
    # "线性表",
    # "顺序表",
    # # "基本运算在顺序表上的实现",
    # "单链表",
    # "双链表",
    # "循环链表",
    # # "线性表的抽象类",
    # # "顺序表类的实现",
    # # "双链表类的实现",
    # "容器 (数据类型)",
    # "迭代器",
    "Vector (STL)",
    "List (STL)",
    # "线性表的应用：文本编辑系统",
    # "栈的顺序实现",
    # "栈的链接实现",
    # "栈的抽象类",
    # "顺序栈类的实现",
    # "链接栈类的实现",
    # "STL 中的栈",
    # "递归消除",
    # "括号配对",
    # "简单的计算器",
    # "队列",
    # "队头位置固定的顺序实现",
    # "队头位置不固定的顺序实现",
    # "循环队列",
    # "队列的链接实现",
    # "队列的抽象类",
    # "循环队列类的实现",
    # "链接队列类的实现",
    # "STL 中的队列",
    # "队列的应用: 排队系统的模拟",
    # "树 (数据结构)",
    # "树的基本术语",
    # # "树的基本运算",
    # "二叉树",
    # "二叉树的主要性质",
    # "二叉树的基本运算和二叉树的遍历",
    # "二叉树的顺序实现",
    # "二叉树的链接实现",
    # "二叉树类的实现",
    # "二叉树遍历的非递归实现",
    # "二叉树的应用：计算表达式",
    # "哈夫曼树",
    # "哈夫曼编码",
    # # "树和森林",
    # # "树的存储实现",
    # # "树的遍历",
    # # "树、林与二叉树的关系",
    # # "基本的优先级队列",
    # "二叉堆",
    # # "二叉堆的有序性",
    # # "基于二叉堆的优先级队列的实现",
    # "D堆",
    # "左堆",
    # "斜堆",
    # "贝努利队列",
    # # "STL 中的优先级队列",
    # # "多服务台排队系统的模拟",
    # "集合",
    # # "查找",
    # "查找表",
    # # "无序表的查找",
    # "顺序查找",
    # # "顺序查找的时间复杂度分析",
    # "二分查找",
    # "插值查找",
    # "分块查找",
    # # "静态查找表的实现",
    # # "STL 中的静态表",
    # # "二叉查找树的定义",
    # "二叉查找树",
    # # "二叉查找树的性能",
    # # "二叉查找树类的实现",
    # "AVL树",
    # # "AVL 树的插入操作",
    # # "AVL 树的删除操作",
    # # "AVL 树类的实现",
    # "红黑树",
    # # "红黑树的插入操作",
    # # "红黑树的删除操作",
    # # "红黑树类的实现",
    # "AA树",
    # "伸展树",
    # # "伸展操作的实现",
    # "B树",
    # "B+树",
    # "set",
    # "关联数组",
    # "散列表",
    # "散列函数",
    # "线性探测法",
    # "二次探测法",
    # "再散列法",
    # "开散列表",
   
    # # "闭散列表的实现" "散列表类的抽象类",,
    # # "开散列表的实现",
    # # "散列表类的应用",
    # "插入排序",
    # # "直接插入排序",
    # # "二分插入排序",
    # "希尔排序",
    # # "希尔排序的性能",
    # "直接选择排序",
    # "堆排序",
    # "冒泡排序",
    # "快速排序",
    # "归并排序",
    # "外排序",
    # # "预处理阶段",
    # # "归并阶段",
    # "等价关系",
    # "等价类",
    # "不相交集",
    # "不相交集的存储实现",
    # "不相交集的运算实现",
    "改进的union算法",
    "改进的find算法",
    # "不相交集类的实现",
    "生成迷宫",
    "最近的共同祖先问题",
    "图(数据结构)",
    # "图的基本术语",
    # "图的基本运算",
    "邻接矩阵",
    "邻接表",
    "深度优先搜索",
    "广度优先搜索",
    "无向图",
    "连通性",
    "欧拉回路",
    "有向图",
    "拓扑排序",
    "生成树",
    "最小生成树",
    "Kruskal算法",
    "Prim算法",
    # "最小生成树算法的正确性",
    "非加权图的最短路径",
    "加权图的最短路径",
    "带有负权值的图",
    "无环图",
    # "所有顶点对的最短路径"
]
for element in content:

    sss='https://zh.wikipedia.org/api/rest_v1/page/summary/{}'
    responseshit=requests.get(sss.format(element))
    gouba=responseshit.json()
    if('extract' not in gouba):
        print ("找不到")
        continue
    tmppair1={
                    "Answer": converter.convert(gouba['extract']),
    "Knowledge_Point": element,
    "Question": "什么是"+element,
    "Tag": "数据结构"
    }
    sstmp="{}.jsonl"
    with jsonlines.open(sstmp.format(element), 'a') as Writer:
        Writer.write( tmppair1)
    


    s='https://zh.wikipedia.org/zh-cn/{}'

    response=requests.get(url=s.format(element))
    tree=etree.HTML(response.text)
    #  title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
    #  question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
    title=tree.xpath('//div[@id="mw-content-text"]//text()')
    # print (title)
    print ("#########################################################")
    s=''
    last=''
    pan=0
    dictionary =[]
    for ele in title:
        s+=ele
    # print (s)
    i=0
    for ele in title:
        i+=1
        if (pan==1):
            if(ele=='\n\n'):
                continue
            if(ele=='\n'):
                continue
            if(ele==' '):
                continue  
            if(ele=='['):
                break

            dictionary.append(ele)
        if(ele=="目录"):
            pan=1
    last=""
    jb=0
    cout=''
    union_of_cout=[]
    ii=0
    pan=0
    i=len(title)
    while (ii<i):
        if (pan==1):
            if(title[ii]=='['):
                if(title[ii+1=="编辑"]):
                    # with open('example.txt', 'a',encoding="utf-8") as f:
                    #     f.write(element+':'+title[ii-1])
                    ii+=3
                    # print(element+':'+last)
                    last=''
                    while(ii!=i-1 and not(title[ii]=='['and title[ii+1]=="编辑")):
                        cout+=last
                        last=title[ii]
                        ii+=1
                    if(ii==i-1):
                        cout+=last
                    union_of_cout.append(cout)
                    # with open('example.txt', 'a',encoding="utf-8") as f:
                    #     f.write(cout)
                    cout=''
                    if(ii==i-1):
                        break
                    ii-=1

            last=title[ii]
        if(title[ii]=="目录"):
            pan=1
        ii+=1

    dic={}
    j=0
    jj=len(dictionary)
    # print (dictionary)
    print (jj)
    jb=''
    i=0
    while(j<jj-1):
        tmp=int(len(dictionary[j])/2)
        j+=1
        dic[tmp]=dictionary[j]
        tmppp=1
        jb=element+"的"+dic[0]
        while(tmppp<=tmp):
            jb+='的'
            jb+=dic[tmppp]
            tmppp+=1
        # print(jb)
        sstmp="{}.jsonl"
        tmppair={
            "Answer": converter.convert(union_of_cout[i]),
    "Knowledge_Point": element,
    "Question": "什么是"+jb,
    "Tag": "数据结构"
        }
        
        with jsonlines.open(sstmp.format(element), 'a') as Writer:
                Writer.write( tmppair)
        # with open('example.txt1', 'a',encoding="utf-8") as f:
        #     f.write(jb+'\n'+"@@@@@@@@@@@@@@@@"+'\n')
        # with open('example.txt1', 'a',encoding="utf-8") as f:
        #     f.write(union_of_cout[i]+'\n'+"@@@@@@@@@@@@@@@@"+'\n')
        print("-------------------------------------------------------------")
        i+=1
        j+=1
    

            




  ```
</details>
<br>
<br>

以下代码是通过`scrapy`框架爬取CSDN中`itcast.py`的代码
<br>
<details>
  <summary>点击展开/收起代码</summary>
  
  ```python

import scrapy
import jsonlines
from lxml import etree
import requests
from mySpider.items import ItcastItem

content = [
    "栈",
    # "数据的逻辑结构",
    "时间复杂度",
    "算法",
    # "渐进表示法",
    # "时间复杂度的计算",
    "面向对象的程序设计",
    # "用面向对象的思想讨论数据结构",
    # "面向对象方法中数据结构的描述与实现",
    "线性表",
    "顺序表",
    # "基本运算在顺序表上的实现",
    "单链表",
    "双链表",
    "循环链表",
    # "线性表的抽象类",
    # "顺序表类的实现",
    # "双链表类的实现",
    "容器 (数据类型)",
    "迭代器",
    "Vector (STL)",
    "List (STL)",
    "线性表的应用：文本编辑系统",
    "栈的顺序实现",
    "栈的链接实现",
    "栈的抽象类",
    "顺序栈类的实现",
    "链接栈类的实现",
    "STL 中的栈",
    "递归消除",
    "括号配对",
    "简单的计算器",
    "队列",
    "队头位置固定的顺序实现",
    "队头位置不固定的顺序实现",
    "循环队列",
    "队列的链接实现",
    "队列的抽象类",
    "循环队列类的实现",
    "链接队列类的实现",
    "STL 中的队列",
    "队列的应用: 排队系统的模拟",
    "树 (数据结构)",
    "树的基本术语",
    # "树的基本运算",
    "二叉树",
    "二叉树的主要性质",
    "二叉树的基本运算和二叉树的遍历",
    "二叉树的顺序实现",
    "二叉树的链接实现",
    "二叉树类的实现",
    "二叉树遍历的非递归实现",
    "二叉树的应用：计算表达式",
    "哈夫曼树",
    "哈夫曼编码",
    # "树和森林",
    # "树的存储实现",
    # "树的遍历",
    # "树、林与二叉树的关系",
    # "基本的优先级队列",
    "二叉堆",
    # "二叉堆的有序性",
    # "基于二叉堆的优先级队列的实现",
    "D堆",
    "左堆",
    "斜堆",
    "贝努利队列",
    # "STL 中的优先级队列",
    # "多服务台排队系统的模拟",
    "集合",
    # "查找",
    "查找表",
    # "无序表的查找",
    "顺序查找",
    # "顺序查找的时间复杂度分析",
    "二分查找",
    "插值查找",
    "分块查找",
    # "静态查找表的实现",
    # "STL 中的静态表",
    # "二叉查找树的定义",
    "二叉查找树",
    # "二叉查找树的性能",
    # "二叉查找树类的实现",
    "AVL树",
    # "AVL 树的插入操作",
    # "AVL 树的删除操作",
    # "AVL 树类的实现",
    "红黑树",
    # "红黑树的插入操作",
    # "红黑树的删除操作",
    # "红黑树类的实现",
    "AA树",
    "伸展树",
    # "伸展操作的实现",
    "B树",
    "B+树",
    "set",
    "关联数组",
    "散列表",
    "散列函数",
    "线性探测法",
    "二次探测法",
    "再散列法",
    "开散列表",
   
    # "闭散列表的实现" "散列表类的抽象类",,
    # "开散列表的实现",
    # "散列表类的应用",
    "插入排序",
    # "直接插入排序",
    # "二分插入排序",
    "希尔排序",
    # "希尔排序的性能",
    "直接选择排序",
    "堆排序",
    "冒泡排序",
    "快速排序",
    "归并排序",
    "外排序",
    # "预处理阶段",
    # "归并阶段",
    "等价关系",
    "等价类",
    "不相交集",
    "不相交集的存储实现",
    "不相交集的运算实现",
    "改进的union算法",
    "改进的find算法",
    # "不相交集类的实现",
    "生成迷宫",
    "最近的共同祖先问题",
    "图(数据结构)",
    # "图的基本术语",
    # "图的基本运算",
    "邻接矩阵",
    "邻接表",
    "深度优先搜索",
    "广度优先搜索",
    "无向图",
    "连通性",
    "欧拉回路",
    "有向图",
    "拓扑排序",
    "生成树",
    "最小生成树",
    "Kruskal算法",
    "Prim算法",
    "最小生成树算法的正确性",
    "非加权图的最短路径",
    "加权图的最短路径",
    "带有负权值的图",
    "无环图",
    "所有顶点对的最短路径"
]
main_url='https://zh.wikipedia.org/wiki/{}'
class ItcastSpider(scrapy.Spider):

    name = "itcast"
    start_urls=[]
    # allowed_domains = ["itcast.cn"]
    def start_requests(self):
        
        for l in range(0,len(content)):
            self.start_urls.append(main_url.format(content[l]))
        for l, url in enumerate(self.start_urls):
            yield scrapy.Request(url, callback=self.parse, cb_kwargs={'l': l})
        # for url in urls:
        #     yield scrapy.Request(url, callback=self.parse)
    # start_urls = ("http://www.itcast.cn/channel/teacher.shtml",)

    def parse(self, response,l):
        sss='https://zh.wikipedia.org/api/rest_v1/page/summary/{}'
        element=content[l]
        responseshit=requests.get(sss.format(element))
        gouba=responseshit.json()
        if('extract' not in gouba):
            print ("找不到")
            return
        tmppair1={
                        "Answer": gouba['extract'],
        "Knowledge_Point": element,
        "Question": "什么是"+element,
        "Tag": "数据结构"
        }
        sstmp="scrapy{}.jsonl"
        with jsonlines.open(sstmp.format(element), 'a') as Writer:
            Writer.write( tmppair1)
    
        tree=etree.HTML(response.text)
        #  title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
        #  question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
        title=tree.xpath('//div[@id="mw-content-text"]//text()')
        # print (title)
        print ("#########################################################")
        s=''
        last=''
        pan=0
        dictionary =[]
        for ele in title:
            s+=ele
        # print (s)
        i=0
        for ele in title:
            i+=1
            if (pan==1):
                if(ele=='\n\n'):
                    continue
                if(ele=='\n'):
                    continue
                if(ele==' '):
                    continue  
                if(ele=='['):
                    break

                dictionary.append(ele)
            if(ele=="目录"):
                pan=1
        last=""
        jb=0
        cout=''
        union_of_cout=[]
        ii=0
        pan=0
        i=len(title)
        while (ii<i):
            if (pan==1):
                if(title[ii]=='['):
                    if(title[ii+1=="编辑"]):
                        # with open('example.txt', 'a',encoding="utf-8") as f:
                        #     f.write(element+':'+title[ii-1])
                        ii+=3
                        # print(element+':'+last)
                        last=''
                        while(ii!=i-1 and not(title[ii]=='['and title[ii+1]=="编辑")):
                            cout+=last
                            last=title[ii]
                            ii+=1
                        if(ii==i-1):
                            cout+=last
                        union_of_cout.append(cout)
                        # with open('example.txt', 'a',encoding="utf-8") as f:
                        #     f.write(cout)
                        cout=''
                        if(ii==i-1):
                            break
                        ii-=1

                last=title[ii]
            if(title[ii]=="目录"):
                pan=1
            ii+=1

        dic={}
        j=0
        jj=len(dictionary)
        # print (dictionary)
        print (jj)
        jb=''
        i=0
        while(j<jj-1):
            tmp=int(len(dictionary[j])/2)
            j+=1
            dic[tmp]=dictionary[j]
            tmppp=1
            jb=element+"的"+dic[0]
            while(tmppp<=tmp):
                jb+='的'
                jb+=dic[tmppp]
                tmppp+=1
            # print(jb)
            sstmp="{}.jsonl"
            tmppair={
                "Answer":union_of_cout[i],
        "Knowledge_Point": element,
        "Question": "什么是"+jb,
        "Tag": "数据结构"
            }
            
            with jsonlines.open(sstmp.format(element), 'a') as Writer:
                    Writer.write( tmppair)
            # with open('example.txt1', 'a',encoding="utf-8") as f:
            #     f.write(jb+'\n'+"@@@@@@@@@@@@@@@@"+'\n')
            # with open('example.txt1', 'a',encoding="utf-8") as f:
            #     f.write(union_of_cout[i]+'\n'+"@@@@@@@@@@@@@@@@"+'\n')
            print("-------------------------------------------------------------")
            i+=1
            j+=1

  ```
</details>

<br>


### STACKOVERFLOW

遇到的主要困难是人机验证。解决的方法很是简朴。

首先自己进行人机验证，然后挂着网页，这样的话在接下来一段时间内（大约5-10分钟）网站不会再次要求人工验证。

这时候我们先把要爬的网页给搞到文件夹里（这些网址再次访问不需要人机验证）就免去了验证的干扰。

<br>
<details>
  <summary>点击展开/收起代码</summary>
  
  ```python


import requests
import json
import jsonlines
from lxml import etree
from opencc import OpenCC
# content = [
#     "栈",
#     "数据的逻辑结构",
#     "时间复杂度",
#     "算法",
#     "渐进表示法",
#     "时间复杂度的计算",
#     "面向对象的程序设计",
#     "用面向对象的思想讨论数据结构",
#     "面向对象方法中数据结构的描述与实现",
#     "线性表",
#     "顺序表",
#     "基本运算在顺序表上的实现",
#     "单链表",
#     "双链表",
#     "循环链表",
#     "线性表的抽象类",
#     "顺序表类的实现",
#     "双链表类的实现",
#     "容器 (数据类型)",
#     "迭代器",
#     "Vector (STL)",
#     "List (STL)",
#     "线性表的应用：文本编辑系统",
#     "栈的顺序实现",
#     "栈的链接实现",
#     "栈的抽象类",
#     "顺序栈类的实现",
#     "链接栈类的实现",
#     "STL 中的栈",
#     "递归消除",
#     "括号配对",
#     "简单的计算器",
#     "队列",
#     "队头位置固定的顺序实现",
#     "队头位置不固定的顺序实现",
#     "循环队列",
#     "队列的链接实现",
#     "队列的抽象类",
#     "循环队列类的实现",
#     "链接队列类的实现",
#     "STL 中的队列",
#     "队列的应用: 排队系统的模拟",
#     "树 (数据结构)",
#     "树的基本术语",
#     "树的基本运算",
#     "二叉树",
#     "二叉树的主要性质",
#     "二叉树的基本运算和二叉树的遍历",
#     "二叉树的顺序实现",
#     "二叉树的链接实现",
#     "二叉树类的实现",
#     "二叉树遍历的非递归实现",
#     "二叉树的应用：计算表达式",
#     "哈夫曼树",
#     "哈夫曼编码",
#     "树和森林",
#     "树的存储实现",
#     "树的遍历",
#     "树、林与二叉树的关系",
#     "基本的优先级队列",
#     "二叉堆",
#     "二叉堆的有序性",
#     "基于二叉堆的优先级队列的实现",
#     "D堆",
#     "左堆",
#     "斜堆",
#     "贝努利队列",
#     "STL 中的优先级队列",
#     "多服务台排队系统的模拟",
#     "集合",
#     "查找",
#     "查找表",
#     "无序表的查找",
#     "顺序查找",
#     "顺序查找的时间复杂度分析",
#     "二分查找",
#     "插值查找",
#     "分块查找",
#     "静态查找表的实现",
#     "STL 中的静态表",
#     "二叉查找树的定义",
#     "二叉查找树",
#     "二叉查找树的性能",
#     "二叉查找树类的实现",
#     "AVL树",
#     "AVL 树的插入操作",
#     "AVL 树的删除操作",
#     "AVL 树类的实现",
#     "红黑树",
#     "红黑树的插入操作",
#     "红黑树的删除操作",
#     "红黑树类的实现",
#     "AA树",
#     "伸展树",
#     "伸展操作的实现",
#     "B树",
#     "B+树",
#     "set",
#     "关联数组",
#     "散列表",
#     "散列函数",
#     "线性探测法",
#     "二次探测法",
#     "再散列法",
#     "开散列表",
   
#     "闭散列表的实现" ,
#     "散列表类的抽象类",
#     "开散列表的实现",
#     "散列表类的应用",
#     "插入排序",
#     "直接插入排序",
#     "二分插入排序",
#     "希尔排序",
#     "希尔排序的性能",
#     "直接选择排序",
#     "堆排序",
#     "冒泡排序",
#     "快速排序",
#     "归并排序",
#     "外排序",
#     "预处理阶段",
#     "归并阶段",
#     "等价关系",
#     "等价类",
#     "不相交集",
#     "不相交集的存储实现",
#     "不相交集的运算实现",
#     "改进的union算法",
#     "改进的find算法",
#     "不相交集类的实现",
#     "生成迷宫",
#     "最近的共同祖先问题",
#     "图(数据结构)",
#     "图的基本术语",
#     "图的基本运算",
#     "邻接矩阵",
#     "邻接表",
#     "深度优先搜索",
#     "广度优先搜索",
#     "无向图",
#     "连通性",
#     "欧拉回路",
#     "有向图",
#     "拓扑排序",
#     "生成树",
#     "最小生成树",
#     "Kruskal算法",
#     "Prim算法",
#     "最小生成树算法的正确性",
#     "非加权图的最短路径",
#     "加权图的最短路径",
#     "带有负权值的图",
#     "无环图",
#     "所有顶点对的最短路径"
# ]




contenteng = [
    # "Stack",
    # "Data-Structure",
    # "Time-Complexity",
    # "Algorithm",
    # "Asymptotic-Notation",
    # "Calculating-Time-Complexity",
    # "Object-Oriented-Programming",
    # "Discussing-Data-Structures-using-OOP",
    # "Description-and-Implementation-of-Data-Structures-in-OOP",
    # "Linear-List",
    # "Sequential-List",
    # "Basic-Operations-on-Sequential-List",
    # "Linked-List",
    # "Doubly-Linked-List",
    # "Circular-Linked-List",
    # "Abstract-Class-for-Linear-Lists",
    # "Implementation-of-Sequential-List-Class",
    # "Implementation-of-Doubly-Linked-List-Class",
    # "Container-(Data-Type)",
    # "Iterator",
    # "Vector-(STL)",
    # "List-(STL)",
    # "Application-of-Linear-List:-Text-Editing-System",
    # "Sequential-Stack-Implementation",
    # "Linked-Stack-Implementation",
    # "Abstract-Class-for-Stack",
    # "Implementation-of-Sequential-Stack-Class",
    # "Implementation-of-Linked-Stack-Class",
    # "Stack-in-STL",
    # "Recursion-Elimination",
    # "Parenthesis-Matching",
    # "Simple-Calculator",
    # "Queue",
    # "Queue-with-Fixed-Front-Position",
    # "Queue-with-Variable-Front-Position",
    # "Circular-Queue",
    # "Linked-Queue",
    # "Abstract-Class-for-Queue",
    # "Implementation-of-Circular-Queue-Class",
    # "Implementation-of-Linked-Queue-Class",
    # "Queue-in-STL",
    # "Application-of-Queue:-Simulation-of-Queuing-System",
    # "Tree-(Data-Structure)",
    # "Basic-Terminologies-of-Tree",
    # "Basic-Operations-on-Tree",
    # "Binary-Tree",
    # "Main-Properties-of-Binary-Tree",
    # "Basic-Operations-and-Traversal-of-Binary-Tree",
    # "Sequential-Implementation-of-Binary-Tree",
    # "Linked-Implementation-of-Binary-Tree",
    # "Implementation-of-Binary-Tree-Class",
    # "Non-Recursive-Traversal-of-Binary-Tree",
    # "Application-of-Binary-Tree:-Expression-Evaluation",
    # "Huffman-Tree",
    # "Huffman-Coding",
    # "Tree-and-Forest",
    # "Storage-Implementation-of-Tree",
    # "Tree-Traversal",
    # "Relationship-between-Tree,-Forest,-and-Binary-Tree",
    # "Basic-Priority-Queue",
    # "Binary-Heap",
    # "Ordering-in-Binary-Heap",
    # "Implementation-of-Priority-Queue-based-on-Binary-Heap",
    # "D-Heap",
    # "Leftist-Heap",
    # "Splay-Tree",
    # "B-Tree",
    # "B+-Tree",
    # "Set",
    # "Associative-Array",
    # "Hash-Table",
    # "Hash-Function",
    # "Linear-Probing",
    # "Quadratic-Probing",
    # "Double-Hashing",
    # "Open-Addressing-Hash-Table",
    # "Closed-Addressing-Hash-Table-Implementation",
    # "Abstract-Class-for-Hash-Table",
    # "Open-Addressing-Hash-Table-Implementation",
    # "Applications-of-Hash-Tables",
    # "Insertion-Sort",
    # "Straight-Insertion-Sort",
    # "Binary-Insertion-Sort",
    # "Shell-Sort",
    # "Performance-of-Shell-Sort",
    # "Selection-Sort",
    # "Heap-Sort",
    # "Bubble-Sort",
    # "Quick-Sort",
    # "Merge-Sort",
    # "External-Sorting",
    # "Preprocessing-Stage",
    # "Merging-Stage",
    # "Equivalence-Relation",
    # "Equivalence-Class",
    # "Disjoint-Set",
    # "Storage-Implementation-of-Disjoint-Set",
    # "Operations-Implementation-for-Disjoint-Set",
    # "Improved-Union-Algorithm",
    # "Improved-Find-Algorithm",
    # "Implementation-of-Disjoint-Set-Class",
    # "Maze-Generation",
    # "Lowest-Common-Ancestor-Problem",
    # "Graph-(Data-Structure)",
    # "Basic-Terminologies-of-Graph",
    # "Basic-Operations-on-Graph",
    # "Adjacency-Matrix",
    # "Adjacency-List",
    # "Depth-First-Search",
    # "Breadth-First-Search",
    # "Undirected-Graph",
    # "Connectivity",
    # "Eulerian-Circuit",
    # "Directed-Graph",
    # "Topological-Sorting",
    # "Spanning-Trees",
    "Minimum-Spanning-Tree",
    # "Kruskal's-Algorithm",
    # "Prim's-Algorithm",
    # "Correctness-of-Minimum-Spanning-Tree-Algorithms",
    # "Shortest-Paths-in-Unweighted-Graph",
    # "Shortest-Paths-in-Weighted-Graph",
    # "Graph-with-Negative-Edge-Weights",
    # "Acyclic-Graph",
    # "All-Pairs-Shortest-Paths"
]


for engele in contenteng:

    url="https://stackoverflow.com/search?page=1&tab=Relevance&pagesize=50&q={}&searchOn=3".format(engele)
    response=requests.get(url=url)
    tree=etree.HTML(response.text)
    #  title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
    #  question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
    title=tree.xpath('//h3[@class="s-post-summary--content-title"]//a/@href')
    total=tree.xpath('//div[@class="flex--item fl1 fs-body3 mr12"]//text()')[0]
    sum=0
    # print(len(total))
    # print (int (total))
    for ele in total:
        if ele>='0' and ele<='9':
            sum*=10
            sum+=int(ele)
    print(sum)

    totalpage=sum//50
    if sum%50:
        totalpage+=1
    print (totalpage)



    print(len(title))
    url="https://stackoverflow.com/search?page={}&tab=Relevance&pagesize=50&q={}&searchOn=3"
    for num in range(1,totalpage+1):
        print ("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`")
        print(url.format(num,engele))
        print ("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`")
        response=requests.get(url=url.format(num,engele))
        tree=etree.HTML(response.text)
        #  title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
        #  question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
        title=tree.xpath('//h3[@class="s-post-summary--content-title"]//a/@href')
        # total=tree.xpath('//div[@class="flex--item fl1 fs-body3 mr12"]//text()')[0]
        for ele in title:
            with jsonlines.open('stackshitflow/shit/{}.jsonl'.format(engele),'a') as Writer:
                Writer.write("https://stackoverflow.com"+ele)
            # print("https://stackoverflow.com"+ele)
    print(engele,"fuck you   end")





  ```
</details>

<br>


当然还有一个细节就是你得将中文关键词转换为英文关键词（这依赖了我们的codemate）

普通代码如下：
<br>
<details>
  <summary>点击展开/收起代码</summary>
  
  ```python


import requests
import json
import jsonlines
from lxml import etree
from opencc import OpenCC
import requests
from urllib3.exceptions import InsecureRequestWarning

# 禁止显示不受信任的 HTTPS 请求警告
requests.packages.urllib3.disable_warnings(category=InsecureRequestWarning)

contenteng = [
    # "Abstract-Class-for-Hash-Table",
    # "Abstract-Class-for-Queue",
    # "Abstract-Class-for-Stack",
    # "Acyclic-Graph",
    # "Adjacency-List",
    # "Adjacency-Matrix",
    # "All-Pairs-Shortest-Paths",
    # "Application-of-Binary-Tree:-Expression-Evaluation",
    # "Application-of-Hash-Tables",
    # "Application-of-Queue:-Simulation-of-Queuing-System",
    # "Basic-Operations-and-Traversal-of-Binary-Tree",
    # "Basic-Operations-on-Graph",
    # "Basic-Priority-Queue",
    # "Basic-Terminologies-of-Graph",
    # "Basic-Terminologies-of-Tree",
    # "Binary-Heap",
    # "Binary-Insertion-Sort",
    # "Binary-Tree",
    # "Bubble-Sort",
    # "B+-Tree",
    # "B-Tree",
    # "Closed-Addressing-Hash-Table-Implementation",
    # "Connectivity",
    # "Correctness-of-Minimum-Spanning-Tree-Algorithms",
    # "D-Heap",
    # "Depth-First-Search",
    # "Directed-Graph",
    # "Disjoint-Set",
    # "Double-Hashing",
    # "Eulerian-Circuit",
    # "Equivalence-Class",
    # "Equivalence-Relation",
    # "External-Sorting",
    # "Graph-(Data-Structure)",
    # "Graph-with-Negative-Edge-Weights",
    # "Hash-Function",
    # "Hash-Table",
    # "Heap-Sort",
    # "Huffman-Coding",
    # "Huffman-Tree",
    # "Implementation-of-Binary-Tree-Class",
    # "Implementation-of-Circular-Queue-Class",
    # "Implementation-of-Disjoint-Set-Class",
    # "Implementation-of-Hash-Table",
    # "Implementation-of-Linked-Queue-Class",
    # "Implementation-of-Priority-Queue-based-on-Binary-Heap",
    # "Implementation-of-Sequential-Stack-Class",
    # "Implementation-of-Linked-Stack-Class",
    # "Improved-Find-Algorithm",
    # "Improved-Union-Algorithm",
    # "Insertion-Sort",
    "Kruskal's-Algorithm",
    "Leftist-Heap",
    "Linear-Probing",
    "Lowest-Common-Ancestor-Problem",
    "Main-Properties-of-Binary-Tree",
    "Maze-Generation",
    "Merge-Sort",
    "Minimum-Spanning-Tree",
    "Non-Recursive-Traversal-of-Binary-Tree",
    "Open-Addressing-Hash-Table-Implementation",
    "Ordering-in-Binary-Heap",
    "Parenthesis-Matching",
    "Performance-of-Shell-Sort",
    "Preprocessing-Stage",
    "Prim's-Algorithm",
    "Queue",
    "Queue-in-STL",
    "Queue-with-Fixed-Front-Position",
    "Queue-with-Variable-Front-Position",
    "Quadratic-Probing",
    "Quick-Sort",
    "Recursion-Elimination",
    # "Relationship-between-Tree,-Forest,-and-Binary-Tree",
    "Sequential-Implementation-of-Binary-Tree",
    "Sequential-Stack-Implementation",
    "Set",
    "Shell-Sort",
    "Shortest-Paths-in-Unweighted-Graph",
    "Shortest-Paths-in-Weighted-Graph",
    "Simple-Calculator",
    "Splay-Tree",
    "Spanning-Trees",
    "Stack-in-STL",
    "Storage-Implementation-of-Disjoint-Set",
    "Storage-Implementation-of-Tree",
    "Straight-Insertion-Sort",
    "Topological-Sorting",
    "Tree-(Data-Structure)",
    "Tree-and-Forest",
    "Tree-Traversal",
    "Undirected-Graph"
]



contenteng1 = [
    # "Stack",
    # "Data-Structure",
    # "Time-Complexity",
    # "Algorithm",
    # "Asymptotic-Notation",
    # "Calculating-Time-Complexity",
    # "Object-Oriented-Programming",
    # "Discussing-Data-Structures-using-OOP",
    # "Description-and-Implementation-of-Data-Structures-in-OOP",
    # "Linear-List",
    # "Sequential-List",
    # "Basic-Operations-on-Sequential-List",
    # "Linked-List",
    # "Doubly-Linked-List",
    # "Circular-Linked-List",
    # "Abstract-Class-for-Linear-Lists",
    # "Implementation-of-Sequential-List-Class",
    # "Implementation-of-Doubly-Linked-List-Class",
    # "Container-(Data-Type)",
    # "Iterator",
    # "Vector-(STL)",
    # "List-(STL)",
    # "Application-of-Linear-List:-Text-Editing-System",
    "Sequential-Stack-Implementation",
    "Linked-Stack-Implementation",
    "Abstract-Class-for-Stack",
    "Implementation-of-Sequential-Stack-Class",
    "Implementation-of-Linked-Stack-Class",
    "Stack-in-STL",
    "Recursion-Elimination",
    "Parenthesis-Matching",
    "Simple-Calculator",
    "Queue",
    "Queue-with-Fixed-Front-Position",
    "Queue-with-Variable-Front-Position",
    "Circular-Queue",
    "Linked-Queue",
    "Abstract-Class-for-Queue",
    "Implementation-of-Circular-Queue-Class",
    "Implementation-of-Linked-Queue-Class",
    "Queue-in-STL",
    "Application-of-Queue:-Simulation-of-Queuing-System",
    "Tree-(Data-Structure)",
    "Basic-Terminologies-of-Tree",
    "Basic-Operations-on-Tree",
    "Binary-Tree",
    "Main-Properties-of-Binary-Tree",
    "Basic-Operations-and-Traversal-of-Binary-Tree",
    "Sequential-Implementation-of-Binary-Tree",
    "Linked-Implementation-of-Binary-Tree",
    "Implementation-of-Binary-Tree-Class",
    "Non-Recursive-Traversal-of-Binary-Tree",
    "Application-of-Binary-Tree:-Expression-Evaluation",
    "Huffman-Tree",
    "Huffman-Coding",
    "Tree-and-Forest",
    "Storage-Implementation-of-Tree",
    "Tree-Traversal",
    "Relationship-between-Tree,-Forest,-and-Binary-Tree",
    "Basic-Priority-Queue",
    "Binary-Heap",
    "Ordering-in-Binary-Heap",
    "Implementation-of-Priority-Queue-based-on-Binary-Heap",
    "D-Heap",
    "Leftist-Heap",
    "Splay-Tree",
    "B-Tree",
    "B+-Tree",
    "Set",
    "Associative-Array",
    "Hash-Table",
    "Hash-Function",
    "Linear-Probing",
    "Quadratic-Probing",
    "Double-Hashing",
    "Open-Addressing-Hash-Table",
    "Closed-Addressing-Hash-Table-Implementation",
    "Abstract-Class-for-Hash-Table",
    "Open-Addressing-Hash-Table-Implementation",
    "Applications-of-Hash-Tables",
    "Insertion-Sort",
    "Straight-Insertion-Sort",
    "Binary-Insertion-Sort",
    "Shell-Sort",
    "Performance-of-Shell-Sort",
    "Selection-Sort",
    "Heap-Sort",
    "Bubble-Sort",
    "Quick-Sort",
    "Merge-Sort",
    "External-Sorting",
    "Preprocessing-Stage",
    "Merging-Stage",
    "Equivalence-Relation",
    "Equivalence-Class",
    "Disjoint-Set",
    "Storage-Implementation-of-Disjoint-Set",
    "Operations-Implementation-for-Disjoint-Set",
    "Improved-Union-Algorithm",
    "Improved-Find-Algorithm",
    "Implementation-of-Disjoint-Set-Class",
    "Maze-Generation",
    "Lowest-Common-Ancestor-Problem",
    "Graph-(Data-Structure)",
    "Basic-Terminologies-of-Graph",
    "Basic-Operations-on-Graph",
    "Adjacency-Matrix",
    "Adjacency-List",
    "Depth-First-Search",
    "Breadth-First-Search",
    "Undirected-Graph",
    "Connectivity",
    "Eulerian-Circuit",
    "Directed-Graph",
    "Topological-Sorting",
    "Spanning-Trees",
    "Minimum-Spanning-Tree",
    "Kruskal's-Algorithm",
    "Prim's-Algorithm",
    "Correctness-of-Minimum-Spanning-Tree-Algorithms",
    "Shortest-Paths-in-Unweighted-Graph",
    "Shortest-Paths-in-Weighted-Graph",
    "Graph-with-Negative-Edge-Weights",
    "Acyclic-Graph",
    "All-Pairs-Shortest-Paths"
]
for elecon in contenteng:
    print(elecon,'begin shit you~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~')
    with jsonlines.open('stackshitflow\shit\{}.jsonl'.format(elecon), 'r') as reader:
        for line in reader:
            print (line)
            url=line
            response=requests.get(url=url, verify=False)
            tree=etree.HTML(response.text)
            #  title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
            question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
            title=tree.xpath('//div[@id="question-header"]//text()')
            # print (title[1])

            que=tree.xpath('//div[@class="postcell post-layout--right"]//div[@class="s-prose js-post-body"]//text()')
            question=title[1]
            for queele in que:
                question+=queele
            # print(question)
            ans=tree.xpath('//div[@id="answers"]/div[@data-position-on-page="1"]//div[@class="s-prose js-post-body"]//text()')
            answer=''
            for ansele in ans:
                answer+=ansele
            # print (answer)

            tmppair={
            "Answer": answer,
    "Knowledge_Point": elecon,
    "Question": question,
    "Tag": "数据结构"
            }

            with jsonlines.open('stackshitflow\dick\{}.jsonl'.format(elecon), 'a') as Writer:
                Writer.write( tmppair)
    print(elecon,'end shit you~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~')




  ```
</details>

<br>


但是由于爬取速度过于感人，所以我们通过`thread`采用多线程以期提高爬虫速度。代码如下:
<br>
<details>
  <summary>点击展开/收起代码</summary>
  
  ```python



import requests
import json
import time
import threading
import jsonlines
from lxml import etree
from opencc import OpenCC
import requests
from urllib3.exceptions import InsecureRequestWarning

# 禁止显示不受信任的 HTTPS 请求警告
requests.packages.urllib3.disable_warnings(category=InsecureRequestWarning)
contenteng = [
    "Kruskal's-Algorithm",
    "Leftist-Heap",
    "Linear-Probing",
    "Lowest-Common-Ancestor-Problem",
    "Main-Properties-of-Binary-Tree",
    "Maze-Generation",
    "Merge-Sort",
    "Minimum-Spanning-Tree",
    "Non-Recursive-Traversal-of-Binary-Tree",
    "Open-Addressing-Hash-Table-Implementation",
    "Ordering-in-Binary-Heap",
    "Parenthesis-Matching",
    "Performance-of-Shell-Sort",
    "Preprocessing-Stage",
    "Prim's-Algorithm",
    "Queue",
    "Queue-in-STL",
    "Queue-with-Fixed-Front-Position",
    "Queue-with-Variable-Front-Position",
    "Quadratic-Probing",
    "Quick-Sort",
    "Recursion-Elimination",
    # "Relationship-between-Tree,-Forest,-and-Binary-Tree",
    "Sequential-Implementation-of-Binary-Tree",
    "Sequential-Stack-Implementation",
    "Set",
    "Shell-Sort",
    "Shortest-Paths-in-Unweighted-Graph",
    "Shortest-Paths-in-Weighted-Graph",
    "Simple-Calculator",
    "Splay-Tree",
    "Spanning-Trees",
    "Stack-in-STL",
    "Storage-Implementation-of-Disjoint-Set",
    "Storage-Implementation-of-Tree",
    "Straight-Insertion-Sort",
    "Topological-Sorting",
    "Tree-(Data-Structure)",
    "Tree-and-Forest",
    "Tree-Traversal",
    "Undirected-Graph"
]
def shityoudick(elecon):
    print(elecon,'begin shit you~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~')
    with jsonlines.open('morethread\shit\{}.jsonl'.format(elecon), 'r') as reader:
        for line in reader:
            print (line)
            url=line
            response=requests.get(url=url, verify=False)
            tree=etree.HTML(response.text)
            #  title=tree.xpath('//section[@class="title-box"]/h1/text()')[0]
            question=tree.xpath('//section[@class="question_show_box"]//div[@class="md_content_show"]//text()')
            title=tree.xpath('//div[@id="question-header"]//text()')
            # print (title[1])

            que=tree.xpath('//div[@class="postcell post-layout--right"]//div[@class="s-prose js-post-body"]//text()')
            question=title[1]
            for queele in que:
                question+=queele
            # print(question)
            ans=tree.xpath('//div[@id="answers"]/div[@data-position-on-page="1"]//div[@class="s-prose js-post-body"]//text()')
            answer=''
            for ansele in ans:
                answer+=ansele
            # print (answer)

            tmppair={
            "Answer": answer,
    "Knowledge_Point": elecon,
    "Question": question,
    "Tag": "数据结构"
            }

            with jsonlines.open('morethread\dick\{}.jsonl'.format(elecon), 'a') as Writer:
                Writer.write( tmppair)
    print(elecon,'end shit you~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~')


poolsema=threading.BoundedSemaphore(2)
thread_list=[]

for elecon in contenteng:
    poolsema.acquire()
    thread=threading.Thread(target=shityoudick, args=[elecon])
    thread.start()
    thread_list.append(thread)
    # thread.join()
    time.sleep(0.2)

    

for t in thread_list:
    t.join()




  ```
</details>

<br>
不过需要注意的是，如果线程过多或者等待时间过短的话，就有很大可能会被封号（需要等30min才能重新连接），所以需要适当调整参数。

## 分类器

## 随机森林

随机森林中我们使用 `jieba` 进行分词。

采取了若干种不同的模型组合尝试。

向量化模型的选择：`TfidfVectorizer`， `Word2Vec`，`CountVectorizer`


分类器的算法实现的选择：`RandomForestClassifier`，`MultinomialNB`，`ComplementNB`

在附上的excel表格中有一些模型组合的相关预测正确率。

经过测验：TfidfVectorizer(), RandomForestClassifier(n_estimators=300, random_state=43)是最好的参数



以下是样例：



<br>
<details>
  <summary>点击展开/收起代码</summary>
  
  ```python



import jieba
import re
import numpy as np
from sklearn.decomposition import PCA
from sklearn.feature_extraction.text import TfidfVectorizer
import gensim
from gensim.models import Word2Vec
import matplotlib.pyplot as plt
import matplotlib
# -*- coding: utf-8 -*-
import json
import jsonlines
import os


stopwords = [
    
    "的", "地", "得", "而", "了", "在", "是", "我", "我们", "你", "您", "他", "她", "它", "他们",
    "她们", "它们", "这", "那", "这里", "那里", "这个", "那个", "之", "与", "以", "及", "或", "同",
    "和", "呢", "吗", "嗯", "啊", "哦", "哈", "喂", "多少", "一些", "一个", "两个", "几个", "好",
    "很", "非常", "不", "没有", "可以", "能", "要", "会", "就", "也", "还", "没", "别", "只", "但",
    "然后", "因为", "所以", "如果", "虽然", "但是", "如何", "什么", "哪些", "怎么", "为什么", "是否",
    "这样", "那样", "这种", "那种", "一样", "那么", "如此", "这些", "那些", "自己", "别人", "每个",
    "一共", "全部", "一部分", "一点", "一种", "一种类型", "例如", "比如", "包括", "等等", "等", "等等。",
    "等等，", "等等...", "等等......", "某个", "某种", "某些", "其它", "其他", "更多", "更少",
    "更好", "更坏", "最好", "最坏", "最多", "最少", "最大", "最小", "最高", "最低", "最近", "最早",
    "最晚", "最新", "最老", "最重要", "最不重要", "最有效", "最无效", "最合适", "最不合适", "越...越...",
    "随着", "关于", "关于...的", "对于", "通过", "采用", "使用", "实现", "完成", "可以使用", "建立",
    "创建", "开发", "编写", "设计", "解决", "处理", "改进", "优化", "增加", "减少", "调整", "更新",
    "删除", "替换", "维护", "管理", "监控", "测试", "调试", "调度", "分析", "评估", "计算", "查找",
    "排序", "过滤", "转换", "比较", "合并", "拆分", "复制", "粘贴", "备份", "恢复", "导入", "导出",
    "下载", "上传", "安装", "卸载", "配置", "设置", "启动", "停止", "求求",
    # 扩展的常见停用词
    "这些都是", "这些都可以", "这些都可能", "以下是", "一些例子", "以下情况", "其他方式", "不同方法", 
    "最重要的是", "最常用的是", "最简单的方法", "最有效的方法", "最好的途径", "最差的情况", "最常见的错误",
    "更详细的信息", "更大的问题", "更好的解决方案", "更准确的结果", "越多越好", "越少越好", "更快速的速度",
    "更高效的算法", "更低的成本", "更长的时间", "更短的时间", "更晚的版本", "更早的日期", "更新的特性",
    "更老的系统", "更强大的功能", "更灵活的选项", "更安全的环境", "更稳定的状态", "更可靠的资源", '\n',
    '(',')','.','\r','，',',','。','！',' ','\r\n',"?",'\t','{','}','//','#','【','】'
    # 添加更多的常见停用词...
]


con=["highQualityTrain","lowQualityTrain","highQualityTest","lowQualityTest"]
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score


# 假设你已经有一个特征向量 X 和对应的标签 Y
rf_classifier = RandomForestClassifier(n_estimators=300, random_state=42)
vectorizer = TfidfVectorizer(stop_words=stopwords,token_pattern='(?u)\\b\\w\\w+\\b')
total_list=[]
for l in range(0,4):
    
# for i in range (1,2):
    # print(l,i)
    if not os.path.exists('训练数据\{}.jsonl'.format(con[l])):
        # print(666)
        break
    
    with jsonlines.open('训练数据\{}.jsonl'.format(con[l]), 'r') as reader:
        
            # 遍历每一行
        for line in reader:
            # 在这里可以修改每一行的值
            text="Question: "+line['Question']+" Answer: "+line['Answer']
            
            seg_list = jieba.lcut(text)

            # filtered_seg_list = [word for word in seg_list if word not in stopwords]
            
            # print(filtered_seg_list)

            total_list.append(" ".join(seg_list))
            # model=gensim.models.Word2Vec(filtered_seg_list, window=5, min_count=1, vector_size=128, workers=4,hs=1,negative=0)
        if(l==1):

            
            # print(total_list)
            X = vectorizer.fit_transform(total_list)
            # print(X)
            y_train1 =[0]*4986+[1] *4753 # 训练集标签
            rf_classifier.fit(X, y_train1)
            total_list=[]
        elif(l==3):
            # vectorizer = TfidfVectorizer()
            
            X = vectorizer.transform(total_list)
            ytest1=[0]*524+[1]*495
            y_pred = rf_classifier.predict(X)
            # 假设 y_true 是真实的标签，y_pred 是模型的预测标签
            accuracy = accuracy_score(ytest1, y_pred)

            print("预测准确率：", accuracy)
            




  ```
</details>

<br>

### BERT
我们用` bert` 预训练模型进行深度学习，构建神经网络。
- 预训练模型的选择
  - `bert-base-chinese`
  -`bert-base-multilingual-uncased`

- learning_rate（`lr`）

  - 1e-3
  - 5e-5
  - 5e-6
  


相关数据见`word`文档

以下是样例代码：



<br>
<details>
  <summary>点击展开/收起代码</summary>
  
  ```python



#!/usr/bin/env python3
#coding=utf-8

from multiprocessing import Pool, Process
from transformers import BertTokenizer, BertModel
from torch.optim import AdamW
import json, torch,jsonlines
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
# train_sum = 0
dataset = []
test_list=[]
con=["highQualityTrain","lowQualityTrain","highQualityTest","lowQualityTest"]

def get_file(file_name, tag):
    with open(file_name, 'r', encoding='utf-8') as f:
        for line in f:
            record = json.loads(line)
            sent_words = "Question: " + ' '.join(record['Question'])
            sent_words += "Answer: " + ' '.join(record['Answer'])
            sent_words.replace('```\n', '[CODE]')
            dataset.append([sent_words, tag])

def get_data():
    # global train_sum
    # get_file("datas/CSDN1.jsonl", 1)
    with jsonlines.open('/content/drive/MyDrive/datas/highQualityTrain.jsonl','r') as reader:

                # 遍历每一行
            for line in reader:
                # 在这里可以修改每一行的值
                # text="Question: "+line['Question']+" Answer: "+line['Answer']
                text="Question: "+' '.join(line['Question'])+" Answer: "+' '.join(line['Answer'])
                # seg_list = jieba.lcut(text)

                # filtered_seg_list = [word for word in seg_list if word not in stopwords]

                # print(filtered_seg_list)

                dataset.append([text,1])
    with jsonlines.open('/content/drive/MyDrive/datas/lowQualityTrain.jsonl','r') as reader:

                # 遍历每一行
            for line in reader:
                # 在这里可以修改每一行的值
                # text="Question: "+line['Question']+" Answer: "+line['Answer']
                text="Question: "+' '.join(line['Question'])+" Answer: "+' '.join(line['Answer'])
                # seg_list = jieba.lcut(text)

                # filtered_seg_list = [word for word in seg_list if word not in stopwords]

                # print(filtered_seg_list)

                dataset.append([text,0])

    with jsonlines.open('/content/drive/MyDrive/datas/highQualityTest.jsonl', 'r') as reader:

                # 遍历每一行
            for line in reader:
                # 在这里可以修改每一行的值
                # text="Question: "+line['Question']+" Answer: "+line['Answer']
                text="Question: "+' '.join(line['Question'])+" Answer: "+' '.join(line['Answer'])
                # seg_list = jieba.lcut(text)

                # filtered_seg_list = [word for word in seg_list if word not in stopwords]

                # print(filtered_seg_list)

                test_list.append([text,1])
    with jsonlines.open('/content/drive/MyDrive/datas/lowQualityTest.jsonl','r') as reader:

                # 遍历每一行
            for line in reader:
                # 在这里可以修改每一行的值
                # text="Question: "+line['Question']+" Answer: "+line['Answer']
                text="Question: "+' '.join(line['Question'])+" Answer: "+' '.join(line['Answer'])
                # seg_list = jieba.lcut(text)

                # filtered_seg_list = [word for word in seg_list if word not in stopwords]

                # print(filtered_seg_list)

                test_list.append([text,0])

def collate(data):
    sents = [i[0] for i in data]
    labels = [i[1] for i in data]
    data = token.batch_encode_plus(batch_text_or_text_pairs=sents,
                                   truncation=True,
                                   padding='max_length',
                                   max_length=512,
                                   return_tensors='pt',
                                   return_length=True)
    input_ids = data['input_ids']
    attention_mask = data['attention_mask']
    token_type_ids = data['token_type_ids']
    labels = torch.LongTensor(labels)
    return input_ids, attention_mask, token_type_ids, labels

class Model(torch.nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = torch.nn.Sequential( torch.nn.Linear(768, 1600), torch.nn.BatchNorm1d(1600), torch.nn.ReLU(True))
        self.fc2 = torch.nn.Sequential( torch.nn.Linear(1600, 800), torch.nn.BatchNorm1d(800), torch.nn.ReLU(True))
        self.fc3 = torch.nn.Sequential( torch.nn.Linear(800, 200), torch.nn.BatchNorm1d(200), torch.nn.ReLU(True))
        self.fc4 = torch.nn.Linear(200, 2)

    def forward(self, input_ids, attention_mask, token_type_ids):
        input_ids = input_ids.to(device)
        attention_mask = attention_mask.to(device)
        token_type_ids = token_type_ids.to(device)
        with torch.no_grad():
            out = pretrained(input_ids=input_ids,
                             attention_mask=attention_mask,
                             token_type_ids=token_type_ids)
        out = out.last_hidden_state[:, 0]
        out = self.fc1(out)
        out = self.fc2(out)
        out = self.fc3(out)
        out = self.fc4(out)
        out = out.softmax(dim=1)
        return out
get_data()
token = BertTokenizer.from_pretrained('bert-base-chinese')
loader = torch.utils.data.DataLoader(dataset=dataset,
                                     batch_size=16,
                                     collate_fn=collate,
                                     shuffle=True,
                                     drop_last=True)

for i, (input_ids, attention_mask, token_type_ids,
        labels) in enumerate(loader):
    input_ids = input_ids.to(device)
    attention_mask = attention_mask.to(device)
    token_type_ids = token_type_ids.to(device)
    labels = labels.to(device)
    break

pretrained = BertModel.from_pretrained('bert-base-chinese').to(device)
for param in pretrained.parameters():
    param.requires_grad_(False)
input_ids, attention_mask, token_type_ids, labels = input_ids.to(device), attention_mask.to(device), token_type_ids.to(device), labels.to(device)
out = pretrained(input_ids=input_ids,
           attention_mask=attention_mask,
           token_type_ids=token_type_ids)




model = Model().to(device)

model.forward(input_ids=input_ids,
      attention_mask=attention_mask,
      token_type_ids=token_type_ids,
      labels=labels)
optimizer = AdamW([{'params': model.parameters()}, {'params': pretrained.parameters()}], lr=5e-4)

# optimizer = AdamW(model.parameters(), lr=5e-4)
criterion = torch.nn.CrossEntropyLoss()


final_accuracy = correct_predictions / total_samples
print("Final Accuracy:", final_accuracy)
def test():
    model.eval()
    correct = 0
    total = 0

    loader_test = torch.utils.data.DataLoader(dataset=test_list,
                                              batch_size=16,
                                              collate_fn=collate,
                                              shuffle=True,
                                              drop_last=True)

    for i, (input_ids, attention_mask, token_type_ids,
            labels) in enumerate(loader_test):

        if i == 100:
            break

        print(i)

        input_ids, attention_mask, token_type_ids, labels = input_ids.to(device), attention_mask.to(device), token_type_ids.to(device), labels.to(device)
        with torch.no_grad():
            out = model.forward(input_ids=input_ids,
            attention_mask=attention_mask,
            token_type_ids=token_type_ids,
            labels=labels)

        out = out.argmax(dim=1)
        correct += (out == labels).sum().item()
        total += len(labels)

    print(correct / total)


test()
test ()

for j in range(60):
    model.train()
    for i, (input_ids, attention_mask, token_type_ids,
            labels) in enumerate(loader):
        input_ids = input_ids.to(device)
        attention_mask = attention_mask.to(device)
        token_type_ids = token_type_ids.to(device)
        labels = labels.to(device)
        out = model(input_ids=input_ids,
                    attention_mask=attention_mask,
                    token_type_ids=token_type_ids)

        loss = criterion(out, labels)
        loss.backward()
        optimizer.step()
        optimizer.zero_grad()
    print("round ", j)
    test()
    test()


  ```
</details>





最后是投票筛选高质量数据：
<br>
<details>
  <summary>点击展开/收起代码</summary>
  
  ```python

import torch, json
from transformers import BertTokenizer, BertModel
dict={}
for i in range (1,100000):
    dict[i]=0
# print (dict)
sum1=0
class Model(torch.nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = torch.nn.Sequential( torch.nn.Linear(768, 1600), torch.nn.BatchNorm1d(1600), torch.nn.ReLU(True))
        self.fc2 = torch.nn.Sequential( torch.nn.Linear(1600, 800), torch.nn.BatchNorm1d(800), torch.nn.ReLU(True))
        self.fc3 = torch.nn.Sequential( torch.nn.Linear(800, 200), torch.nn.BatchNorm1d(200), torch.nn.ReLU(True))
        self.fc4 = torch.nn.Linear(200, 2)

    def forward(self, input_ids, attention_mask, token_type_ids):
        input_ids = input_ids.to(device)
        attention_mask = attention_mask.to(device)
        token_type_ids = token_type_ids.to(device)
        with torch.no_grad():
            out = pretrained(input_ids=input_ids,
                    attention_mask=attention_mask,
                    token_type_ids=token_type_ids)
        out = out.last_hidden_state[:, 0]
        out = self.fc1(out)
        out = self.fc2(out)
        out = self.fc3(out)
        out = self.fc4(out)
        out = out.softmax(dim=1)
        return out

dataset_train = []
dataset_test = []

def fecth_file(file_name, tag, a):
    with open(file_name, 'r', encoding='utf-8') as f:
        for line in f:
            tmp_dict = json.loads(line)
            content = "Question: " + ' '.join(tmp_dict['Question'])
            content += "Answer: " + ' '.join(tmp_dict['Answer'])
            if a == 1:
                dataset_train.append([content, tag])
            else:
                dataset_test.append([content, tag])

def load_test_data():
    fecth_file("/kaggle/input/merging/merged123123214134134134113213123213123.jsonl", 1, 2)

# 加载预训练模型和分词器
pretrained = BertModel.from_pretrained('bert-base-chinese')
token = BertTokenizer.from_pretrained('bert-base-chinese')
model = Model()
model.load_state_dict(torch.load("/kaggle/input/mymodel/0.pt"))
device = torch.device("cpu" if torch.cuda.is_available() else "cpu")
model.to(device)

# 设置设备
def collate_fn(data):
    sents = [i[0] for i in data]
    labels = [i[1] for i in data]
    data = token.batch_encode_plus(batch_text_or_text_pairs=sents,
                                   truncation=True,
                                   padding='max_length',
                                   max_length=500,
                                   return_tensors='pt',
                                   return_length=True)
    input_ids = data['input_ids']
    attention_mask = data['attention_mask']
    token_type_ids = data['token_type_ids']
    labels = torch.LongTensor(labels)
    return input_ids, attention_mask, token_type_ids, labels

# 准备输入文本
# input_text = "这是一段待分类的文本"
load_test_data()

print("test begin!")
model.eval()
correct = 0
total = 0
loader_test = torch.utils.data.DataLoader(dataset=dataset_test,
                                          batch_size=1,
                                          collate_fn=collate_fn,
                                          shuffle=False,
                                          drop_last=True)
print ("model1begin")
for i, (input_ids, attention_mask, token_type_ids,
        labels) in enumerate(loader_test):
    
    sum1+=1
#     print (sum1)
#     print(labels)
#     print (dataset)
    input_ids = input_ids.to(device)
    attention_mask = attention_mask.to(device)
    token_type_ids = token_type_ids.to(device)
    labels = labels.to(device)

    with torch.no_grad():
        out = model(input_ids=input_ids,
                    attention_mask=attention_mask,
                    token_type_ids=token_type_ids)

    out = out.argmax(dim=1)
#     print(out)
    correct += (out == labels).sum().item()
    total += len(labels)
#     print (sum1)
    if out==labels:
        dict[sum1]+=1
#     print("the accurate rate is ", end = "")
#     print(correct / total)
#     print (dict)

# 加载保存的模型权重参数
# model = BertModel.from_pretrained('bert-base-chinese')
# model.load_state_dict(torch.load("/kaggle/input/mymodel/0.pt"))
# model.eval()
    
# # 使用模型进行推理
# with torch.no_grad():
#     outputs = model(input_ids=input_ids, attention_mask=attention_mask,token_type_ids=token_type_ids)

# # 处理输出结果
# predictions = torch.argmax(outputs.logits, dim=1)
# predicted_label = predictions.item()

# 打印预测结果
# print("Input Text:", input_text)
# print("Predicted Label:", predicted_label)





sum1=0
class Model(torch.nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = torch.nn.Sequential( torch.nn.Linear(768, 1600), torch.nn.BatchNorm1d(1600), torch.nn.ReLU(True))
        self.fc2 = torch.nn.Sequential( torch.nn.Linear(1600, 800), torch.nn.BatchNorm1d(800), torch.nn.ReLU(True))
        self.fc3 = torch.nn.Sequential( torch.nn.Linear(800, 200), torch.nn.BatchNorm1d(200), torch.nn.ReLU(True))
        self.fc4 = torch.nn.Linear(200, 2)

    def forward(self, input_ids, attention_mask, token_type_ids):
        input_ids = input_ids.to(device)
        attention_mask = attention_mask.to(device)
        token_type_ids = token_type_ids.to(device)
        with torch.no_grad():
            out = pretrained(input_ids=input_ids,
                    attention_mask=attention_mask,
                    token_type_ids=token_type_ids)
        out = out.last_hidden_state[:, 0]
        out = self.fc1(out)
        out = self.fc2(out)
        out = self.fc3(out)
        out = self.fc4(out)
        out = out.softmax(dim=1)
        return out

dataset_train = []
dataset_test = []

def fecth_file(file_name, tag, a):
    with open(file_name, 'r', encoding='utf-8') as f:
        for line in f:
            tmp_dict = json.loads(line)
            content = "Question: " + ' '.join(tmp_dict['Question'])
            content += "Answer: " + ' '.join(tmp_dict['Answer'])
            if a == 1:
                dataset_train.append([content, tag])
            else:
                dataset_test.append([content, tag])

def load_test_data():
    fecth_file("/kaggle/input/merging/merged123123214134134134113213123213123.jsonl", 0, 2)

# 加载预训练模型和分词器
pretrained = BertModel.from_pretrained('bert-base-chinese')
token = BertTokenizer.from_pretrained('bert-base-chinese')
model = Model()
model.load_state_dict(torch.load("/kaggle/input/mymodel/12_1.pt"))
device = torch.device("cpu" if torch.cuda.is_available() else "cpu")
model.to(device)

# 设置设备
def collate_fn(data):
    sents = [i[0] for i in data]
    labels = [i[1] for i in data]
    data = token.batch_encode_plus(batch_text_or_text_pairs=sents,
                                   truncation=True,
                                   padding='max_length',
                                   max_length=500,
                                   return_tensors='pt',
                                   return_length=True)
    input_ids = data['input_ids']
    attention_mask = data['attention_mask']
    token_type_ids = data['token_type_ids']
    labels = torch.LongTensor(labels)
    return input_ids, attention_mask, token_type_ids, labels

# 准备输入文本
# input_text = "这是一段待分类的文本"
load_test_data()

print("test begin!")
model.eval()
correct = 0
total = 0
loader_test = torch.utils.data.DataLoader(dataset=dataset_test,
                                          batch_size=1,
                                          collate_fn=collate_fn,
                                          shuffle=False,
                                          drop_last=True)
print ("model2begin")
for i, (input_ids, attention_mask, token_type_ids,
        labels) in enumerate(loader_test):
    
    sum1+=1
#     print (sum1)
#     print(labels)
#     print (dataset)
    input_ids = input_ids.to(device)
    attention_mask = attention_mask.to(device)
    token_type_ids = token_type_ids.to(device)
    labels = labels.to(device)

    with torch.no_grad():
        out = model(input_ids=input_ids,
                    attention_mask=attention_mask,
                    token_type_ids=token_type_ids)

    out = out.argmax(dim=1)
#     print(out)
    correct += (out == labels).sum().item()
    total += len(labels)
    if out==labels:
        dict[sum1]+=1
#     print("the accurate rate is ", end = "")
#     print(correct / total)
#     print (dict)

    
    
    
sum1=0
class Model(torch.nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = torch.nn.Sequential( torch.nn.Linear(768, 1600), torch.nn.BatchNorm1d(1600), torch.nn.ReLU(True))
        self.fc2 = torch.nn.Sequential( torch.nn.Linear(1600, 800), torch.nn.BatchNorm1d(800), torch.nn.ReLU(True))
        self.fc3 = torch.nn.Sequential( torch.nn.Linear(800, 200), torch.nn.BatchNorm1d(200), torch.nn.ReLU(True))
        self.fc4 = torch.nn.Linear(200, 2)

    def forward(self, input_ids, attention_mask, token_type_ids):
        input_ids = input_ids.to(device)
        attention_mask = attention_mask.to(device)
        token_type_ids = token_type_ids.to(device)
        with torch.no_grad():
            out = pretrained(input_ids=input_ids,
                    attention_mask=attention_mask,
                    token_type_ids=token_type_ids)
        out = out.last_hidden_state[:, 0]
        out = self.fc1(out)
        out = self.fc2(out)
        out = self.fc3(out)
        out = self.fc4(out)
        out = out.softmax(dim=1)
        return out

dataset_train = []
dataset_test = []

def fecth_file(file_name, tag, a):
    with open(file_name, 'r', encoding='utf-8') as f:
        for line in f:
            tmp_dict = json.loads(line)
            content = "Question: " + ' '.join(tmp_dict['Question'])
            content += "Answer: " + ' '.join(tmp_dict['Answer'])
            if a == 1:
                dataset_train.append([content, tag])
            else:
                dataset_test.append([content, tag])

def load_test_data():
    fecth_file("/kaggle/input/merging/merged123123214134134134113213123213123.jsonl", 1, 2)


# 加载预训练模型和分词器
pretrained = BertModel.from_pretrained('bert-base-chinese')
token = BertTokenizer.from_pretrained('bert-base-chinese')
model = Model()
model.load_state_dict(torch.load("/kaggle/input/mymodel/12_2.pt"))
device = torch.device("cpu" if torch.cuda.is_available() else "cpu")
model.to(device)

# 设置设备
def collate_fn(data):
    sents = [i[0] for i in data]
    labels = [i[1] for i in data]
    data = token.batch_encode_plus(batch_text_or_text_pairs=sents,
                                   truncation=True,
                                   padding='max_length',
                                   max_length=500,
                                   return_tensors='pt',
                                   return_length=True)
    input_ids = data['input_ids']
    attention_mask = data['attention_mask']
    token_type_ids = data['token_type_ids']
    labels = torch.LongTensor(labels)
    return input_ids, attention_mask, token_type_ids, labels

# 准备输入文本
# input_text = "这是一段待分类的文本"
load_test_data()

print("test begin!")
model.eval()
correct = 0
total = 0
loader_test = torch.utils.data.DataLoader(dataset=dataset_test,
                                          batch_size=1,
                                          collate_fn=collate_fn,
                                          shuffle=False,
                                          drop_last=True)
print ("model3begin")
for i, (input_ids, attention_mask, token_type_ids,
        labels) in enumerate(loader_test):
    
    sum1+=1
#     print (sum)1
#     print(labels)
#     print (dataset)
    input_ids = input_ids.to(device)
    attention_mask = attention_mask.to(device)
    token_type_ids = token_type_ids.to(device)
    labels = labels.to(device)

    with torch.no_grad():
        out = model(input_ids=input_ids,
                    attention_mask=attention_mask,
                    token_type_ids=token_type_ids)

    out = out.argmax(dim=1)
#     print(out)
    correct += (out == labels).sum().item()
    total += len(labels)
    if out==labels:
        dict[sum1]+=1
#     print("the accurate rate is ", end = "")
#     print(correct / total)
#     print (dict)
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
# 随机森林





print ("rf1")

            




import jieba
import re
import numpy as np
from sklearn.decomposition import PCA
from sklearn.feature_extraction.text import TfidfVectorizer
import gensim
from gensim.models import Word2Vec
import matplotlib.pyplot as plt
import matplotlib
# -*- coding: utf-8 -*-
import json
import jsonlines
import os


stopwords = [
        '我',
    '你',
    '的',
    '得',
    '地',
    '是',
    '在',
    '我们',
    '你们',
    '他们',
    '和',
    '或者',
    '但是',
    '如果',
    '它们',
    '一些',
    '有',
    '不',
    '这',
    '那',
    '哪',
    '如何',
    '怎么样',
    '了',
    '吗',
    '呢',
    '啊',
    '这个',
    '那个',
    '一样',
    '所有',
    '没有',
    '不是',
    '可以',
    '能够',
    '是不是',
    '是否',
    '自己',
    '之前',
    '之后',
    '到底',
    '这样',
    '那样',
    '如何',
    '怎么',
    '多少',
    "的", "地", "得", "而", 
    "了", "在", "是", "我", "我们", "你", "您", "他", "她", "它", "他们",
    "她们", "它们", "这", 
    "那", "这里", "那里", "这个", "那个", "之", "与", "以", "及", "或", "同",
    "和", "呢", "吗", "嗯", 
    "啊", "哦", "哈", "喂", "多少", "一些", "一个", "两个", "几个", "好",
    "很", "非常", "不", "没有", "可以", "能", "要", "会", "就", "也", "还", "没", "别", "只", "但",
    "然后", "因为", "所以", "如果", "虽然", "但是", "如何", "什么", "哪些", "怎么", "为什么", "是否",
    "这样", "那样", "这种", "那种", "一样", "那么", "如此", "这些", "那些", "自己", "别人", "每个",
    "一共", "全部", "一部分", "一点", "一种", "一种类型", "例如", "比如", "包括", "等等", "等", "等等。",
    "等等，", "等等...", "等等......", "某个", "某种", "某些", "其它", "其他", "更多", "更少",
    "更好", "更坏", "最好", "最坏", "最多", "最少", "最大", "最小", "最高", "最低", "最近", "最早",
    "最晚", "最新", "最老", "最重要", "最不重要", "最有效", "最无效", "最合适", "最不合适", "越...越...",
    "随着", "关于", "关于...的", 
    "对于", "通过", "采用", "使用", "实现", "完成", "可以使用", "建立",
    "创建", "开发", "编写", "设计", "解决", "处理", "改进", "优化", "增加", "减少", "调整", "更新",
    "删除", "替换", "维护", 
    "管理", "监控", "测试", "调试", "调度", "分析", "评估", "计算", "查找",
    "排序", "过滤", "转换", "比较", "合并", "拆分", "复制", "粘贴", "备份", "恢复", "导入", "导出",
    "下载", "上传", "安装",
      "卸载", "配置", "设置", "启动", "停止", "求求",
    # 扩展的常见停用词
    "这些都是", "这些都可以", "这些都可能", "以下是", "一些例子", "以下情况", "其他方式", "不同方法", 
    "最重要的是", "最常用的是", 
    "最简单的方法", "最有效的方法", "最好的途径", "最差的情况", "最常见的错误",
    "更详细的信息", "更大的问题",
      "更好的解决方案", "更准确的结果", "越多越好", "越少越好", "更快速的速度",
    "更高效的算法", "更低的成本", "更长的时间", "更短的时间", "更晚的版本", "更早的日期", "更新的特性",
    "更老的系统", "更强大的功能",
      "更灵活的选项", "更安全的环境", "更稳定的状态", "更可靠的资源", '\n',
    '(',')','.','\r','，',',','。','！',' ','\r\n',"?",'\t','{','}','//','#','【','】'
    # 添加更多的常见停用词...
]


con=["/kaggle/input/shit123/训练数据/highQualityTrain.jsonl","/kaggle/input/shit123/训练数据/lowQualityTrain.jsonl","/kaggle/input/merging/merged123123214134134134113213123213123.jsonl"]
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score


# 假设你已经有一个特征向量 X 和对应的标签 Y
rf_classifier = RandomForestClassifier(n_estimators=300, random_state=42)
vectorizer = TfidfVectorizer(stop_words=stopwords,token_pattern='(?u)\\b\\w\\w+\\b')
total_list=[]
for l in range(0,3):
    with jsonlines.open(con[l], 'r') as reader:
            # 遍历每一行
        for line in reader:
            # 在这里可以修改每一行的值
            text="Question: "+line['Question']+" Answer: "+line['Answer']
            
            seg_list = jieba.lcut(text)

            total_list.append(" ".join(seg_list))
            # model=gensim.models.Word2Vec(filtered_seg_list, window=5, min_count=1, vector_size=128, workers=4,hs=1,negative=0)
        if(l==1):

            
            # print(total_list)
            X = vectorizer.fit_transform(total_list)
            # print(X)
            y_train1 =[0]*4986+[1] *4753 # 训练集标签
            rf_classifier.fit(X, y_train1)
            total_list=[]
        elif(l==2):
            # vectorizer = TfidfVectorizer()
            
            X = vectorizer.transform(total_list)
#             ytest1=[0]*524+[1]*495
            y_pred = rf_classifier.predict(X)
            for jj in range (1,len(y_pred)+1):
#                 print (y_pred[jj])
                if(y_pred[jj-1]==1):
                    dict[jj]+=1
            # 假设 y_true 是真实的标签，y_pred 是模型的预测标签
#             accuracy = accuracy_score(ytest1, y_pred)

#             print("预测准确率：", accuracy)
            



print ("rf2")
    
    
    
    
    
    
stopwords = [
        '我',
    '你',
    '的',
    '得',
    '地',
    '是',
    '在',
    '我们',
    '你们',
    '他们',
    '和',
    '或者',
    '但是',
    '如果',
    '它们',
    '一些',
    '有',
    '不',
    '这',
    '那',
    '哪',
    '如何',
    '怎么样',
    '了',
    '吗',
    '呢',
    '啊',
    '这个',
    '那个',
    '一样',
    '所有',
    '没有',
    '不是',
    '可以',
    '能够',
    '是不是',
    '是否',
    '自己',
    '之前',
    '之后',
    '到底',
    '这样',
    '那样',
    '如何',
    '怎么',
    '多少',
    "的", "地", "得", "而", 
    "了", "在", "是", "我", "我们", "你", "您", "他", "她", "它", "他们",
    "她们", "它们", "这", 
    "那", "这里", "那里", "这个", "那个", "之", "与", "以", "及", "或", "同",
    "和", "呢", "吗", "嗯", 
    "啊", "哦", "哈", "喂", "多少", "一些", "一个", "两个", "几个", "好",
    "很", "非常", "不", "没有", "可以", "能", "要", "会", "就", "也", "还", "没", "别", "只", "但",
    "然后", "因为", "所以", "如果", "虽然", "但是", "如何", "什么", "哪些", "怎么", "为什么", "是否",
    "这样", "那样", "这种", "那种", "一样", "那么", "如此", "这些", "那些", "自己", "别人", "每个",
    "一共", "全部", "一部分", "一点", "一种", "一种类型", "例如", "比如", "包括", "等等", "等", "等等。",
    "等等，", "等等...", "等等......", "某个", "某种", "某些", "其它", "其他", "更多", "更少",
    "更好", "更坏", "最好", "最坏", "最多", "最少", "最大", "最小", "最高", "最低", "最近", "最早",
    "最晚", "最新", "最老", "最重要", "最不重要", "最有效", "最无效", "最合适", "最不合适", "越...越...",
    "随着", "关于", "关于...的", 
    "对于", "通过", "采用", "使用", "实现", "完成", "可以使用", "建立",
    "创建", "开发", "编写", "设计", "解决", "处理", "改进", "优化", "增加", "减少", "调整", "更新",
    "删除", "替换", "维护", 
    "管理", "监控", "测试", "调试", "调度", "分析", "评估", "计算", "查找",
    "排序", "过滤", "转换", "比较", "合并", "拆分", "复制", "粘贴", "备份", "恢复", "导入", "导出",
    "下载", "上传", "安装",
      "卸载", "配置", "设置", "启动", "停止", "求求",
    # 扩展的常见停用词
    "这些都是", "这些都可以", "这些都可能", "以下是", "一些例子", "以下情况", "其他方式", "不同方法", 
    "最重要的是", "最常用的是", 
    "最简单的方法", "最有效的方法", "最好的途径", "最差的情况", "最常见的错误",
    "更详细的信息", "更大的问题",
      "更好的解决方案", "更准确的结果", "越多越好", "越少越好", "更快速的速度",
    "更高效的算法", "更低的成本", "更长的时间", "更短的时间", "更晚的版本", "更早的日期", "更新的特性",
    "更老的系统", "更强大的功能",
      "更灵活的选项", "更安全的环境", "更稳定的状态", "更可靠的资源", '\n',
    '(',')','.','\r','，',',','。','！',' ','\r\n',"?",'\t','{','}','//','#','【','】'
    # 添加更多的常见停用词...
]


con=["/kaggle/input/shit123/训练数据/highQualityTrain.jsonl","/kaggle/input/shit123/训练数据/lowQualityTrain.jsonl","/kaggle/input/merging/merged123123214134134134113213123213123.jsonl"]
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score


# 假设你已经有一个特征向量 X 和对应的标签 Y
rf_classifier = RandomForestClassifier(n_estimators=250, random_state=42)
vectorizer = TfidfVectorizer(stop_words=stopwords,token_pattern='(?u)\\b\\w\\w+\\b')
total_list=[]
for l in range(0,3):
    with jsonlines.open(con[l], 'r') as reader:
            # 遍历每一行
        for line in reader:
            # 在这里可以修改每一行的值
            text="Question: "+line['Question']+" Answer: "+line['Answer']
            
            seg_list = jieba.lcut(text)

            total_list.append(" ".join(seg_list))
            # model=gensim.models.Word2Vec(filtered_seg_list, window=5, min_count=1, vector_size=128, workers=4,hs=1,negative=0)
        if(l==1):

            
            # print(total_list)
            X = vectorizer.fit_transform(total_list)
            # print(X)
            y_train1 =[0]*4986+[1] *4753 # 训练集标签
            rf_classifier.fit(X, y_train1)
            total_list=[]
        elif(l==2):
            # vectorizer = TfidfVectorizer()
            
            X = vectorizer.transform(total_list)
#             ytest1=[0]*524+[1]*495
            y_pred = rf_classifier.predict(X)
            for jj in range (1,len(y_pred)+1):
#                 print (y_pred[jj])
                if(y_pred[jj-1]==0):
                    dict[jj]+=1
            # 假设 y_true 是真实的标签，y_pred 是模型的预测标签
#             accuracy = accuracy_score(ytest1, y_pred)

#             print("预测准确率：", accuracy)
            
    
    
    
    
print ("rf3")
    
    
    
stopwords = [
        '我',
    '你',
    '的',
    '得',
    '地',
    '是',
    '在',
    '我们',
    '你们',
    '他们',
    '和',
    '或者',
    '但是',
    '如果',
    '它们',
    '一些',
    '有',
    '不',
    '这',
    '那',
    '哪',
    '如何',
    '怎么样',
    '了',
    '吗',
    '呢',
    '啊',
    '这个',
    '那个',
    '一样',
    '所有',
    '没有',
    '不是',
    '可以',
    '能够',
    '是不是',
    '是否',
    '自己',
    '之前',
    '之后',
    '到底',
    '这样',
    '那样',
    '如何',
    '怎么',
    '多少',
    "的", "地", "得", "而", 
    "了", "在", "是", "我", "我们", "你", "您", "他", "她", "它", "他们",
    "她们", "它们", "这", 
    "那", "这里", "那里", "这个", "那个", "之", "与", "以", "及", "或", "同",
    "和", "呢", "吗", "嗯", 
    "啊", "哦", "哈", "喂", "多少", "一些", "一个", "两个", "几个", "好",
    "很", "非常", "不", "没有", "可以", "能", "要", "会", "就", "也", "还", "没", "别", "只", "但",
    "然后", "因为", "所以", "如果", "虽然", "但是", "如何", "什么", "哪些", "怎么", "为什么", "是否",
    "这样", "那样", "这种", "那种", "一样", "那么", "如此", "这些", "那些", "自己", "别人", "每个",
    "一共", "全部", "一部分", "一点", "一种", "一种类型", "例如", "比如", "包括", "等等", "等", "等等。",
    "等等，", "等等...", "等等......", "某个", "某种", "某些", "其它", "其他", "更多", "更少",
    "更好", "更坏", "最好", "最坏", "最多", "最少", "最大", "最小", "最高", "最低", "最近", "最早",
    "最晚", "最新", "最老", "最重要", "最不重要", "最有效", "最无效", "最合适", "最不合适", "越...越...",
    "随着", "关于", "关于...的", 
    "对于", "通过", "采用", "使用", "实现", "完成", "可以使用", "建立",
    "创建", "开发", "编写", "设计", "解决", "处理", "改进", "优化", "增加", "减少", "调整", "更新",
    "删除", "替换", "维护", 
    "管理", "监控", "测试", "调试", "调度", "分析", "评估", "计算", "查找",
    "排序", "过滤", "转换", "比较", "合并", "拆分", "复制", "粘贴", "备份", "恢复", "导入", "导出",
    "下载", "上传", "安装",
      "卸载", "配置", "设置", "启动", "停止", "求求",
    # 扩展的常见停用词
    "这些都是", "这些都可以", "这些都可能", "以下是", "一些例子", "以下情况", "其他方式", "不同方法", 
    "最重要的是", "最常用的是", 
    "最简单的方法", "最有效的方法", "最好的途径", "最差的情况", "最常见的错误",
    "更详细的信息", "更大的问题",
      "更好的解决方案", "更准确的结果", "越多越好", "越少越好", "更快速的速度",
    "更高效的算法", "更低的成本", "更长的时间", "更短的时间", "更晚的版本", "更早的日期", "更新的特性",
    "更老的系统", "更强大的功能",
      "更灵活的选项", "更安全的环境", "更稳定的状态", "更可靠的资源", '\n',
    '(',')','.','\r','，',',','。','！',' ','\r\n',"?",'\t','{','}','//','#','【','】'
    # 添加更多的常见停用词...
]


con=["/kaggle/input/shit123/训练数据/highQualityTrain.jsonl","/kaggle/input/shit123/训练数据/lowQualityTrain.jsonl","/kaggle/input/merging/merged123123214134134134113213123213123.jsonl"]
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score


# 假设你已经有一个特征向量 X 和对应的标签 Y
rf_classifier = RandomForestClassifier(n_estimators=200, random_state=42)
vectorizer = TfidfVectorizer(stop_words=stopwords,token_pattern='(?u)\\b\\w\\w+\\b')
total_list=[]
for l in range(0,3):
    with jsonlines.open(con[l], 'r') as reader:
            # 遍历每一行
        for line in reader:
            # 在这里可以修改每一行的值
            text="Question: "+line['Question']+" Answer: "+line['Answer']
            
            seg_list = jieba.lcut(text)

            total_list.append(" ".join(seg_list))
            # model=gensim.models.Word2Vec(filtered_seg_list, window=5, min_count=1, vector_size=128, workers=4,hs=1,negative=0)
        if(l==1):

            
            # print(total_list)
            X = vectorizer.fit_transform(total_list)
            # print(X)
            y_train1 =[0]*4986+[1] *4753 # 训练集标签
            rf_classifier.fit(X, y_train1)
            total_list=[]
        elif(l==2):
            # vectorizer = TfidfVectorizer()
            
            X = vectorizer.transform(total_list)
#             ytest1=[0]*524+[1]*495
            y_pred = rf_classifier.predict(X)
            for jj in range (1,len(y_pred)+1):
#                 print (y_pred[jj])
                if(y_pred[jj-1]==0):
                    dict[jj]+=1
            # 假设 y_true 是真实的标签，y_pred 是模型的预测标签
#             accuracy = accuracy_score(ytest1, y_pred)

#             print("预测准确率：", accuracy)


    
    
print ("rf4")





stopwords = [
        '我',
    '你',
    '的',
    '得',
    '地',
    '是',
    '在',
    '我们',
    '你们',
    '他们',
    '和',
    '或者',
    '但是',
    '如果',
    '它们',
    '一些',
    '有',
    '不',
    '这',
    '那',
    '哪',
    '如何',
    '怎么样',
    '了',
    '吗',
    '呢',
    '啊',
    '这个',
    '那个',
    '一样',
    '所有',
    '没有',
    '不是',
    '可以',
    '能够',
    '是不是',
    '是否',
    '自己',
    '之前',
    '之后',
    '到底',
    '这样',
    '那样',
    '如何',
    '怎么',
    '多少',
    "的", "地", "得", "而", 
    "了", "在", "是", "我", "我们", "你", "您", "他", "她", "它", "他们",
    "她们", "它们", "这", 
    "那", "这里", "那里", "这个", "那个", "之", "与", "以", "及", "或", "同",
    "和", "呢", "吗", "嗯", 
    "啊", "哦", "哈", "喂", "多少", "一些", "一个", "两个", "几个", "好",
    "很", "非常", "不", "没有", "可以", "能", "要", "会", "就", "也", "还", "没", "别", "只", "但",
    "然后", "因为", "所以", "如果", "虽然", "但是", "如何", "什么", "哪些", "怎么", "为什么", "是否",
    "这样", "那样", "这种", "那种", "一样", "那么", "如此", "这些", "那些", "自己", "别人", "每个",
    "一共", "全部", "一部分", "一点", "一种", "一种类型", "例如", "比如", "包括", "等等", "等", "等等。",
    "等等，", "等等...", "等等......", "某个", "某种", "某些", "其它", "其他", "更多", "更少",
    "更好", "更坏", "最好", "最坏", "最多", "最少", "最大", "最小", "最高", "最低", "最近", "最早",
    "最晚", "最新", "最老", "最重要", "最不重要", "最有效", "最无效", "最合适", "最不合适", "越...越...",
    "随着", "关于", "关于...的", 
    "对于", "通过", "采用", "使用", "实现", "完成", "可以使用", "建立",
    "创建", "开发", "编写", "设计", "解决", "处理", "改进", "优化", "增加", "减少", "调整", "更新",
    "删除", "替换", "维护", 
    "管理", "监控", "测试", "调试", "调度", "分析", "评估", "计算", "查找",
    "排序", "过滤", "转换", "比较", "合并", "拆分", "复制", "粘贴", "备份", "恢复", "导入", "导出",
    "下载", "上传", "安装",
      "卸载", "配置", "设置", "启动", "停止", "求求",
    # 扩展的常见停用词
    "这些都是", "这些都可以", "这些都可能", "以下是", "一些例子", "以下情况", "其他方式", "不同方法", 
    "最重要的是", "最常用的是", 
    "最简单的方法", "最有效的方法", "最好的途径", "最差的情况", "最常见的错误",
    "更详细的信息", "更大的问题",
      "更好的解决方案", "更准确的结果", "越多越好", "越少越好", "更快速的速度",
    "更高效的算法", "更低的成本", "更长的时间", "更短的时间", "更晚的版本", "更早的日期", "更新的特性",
    "更老的系统", "更强大的功能",
      "更灵活的选项", "更安全的环境", "更稳定的状态", "更可靠的资源", '\n',
    '(',')','.','\r','，',',','。','！',' ','\r\n',"?",'\t','{','}','//','#','【','】'
    # 添加更多的常见停用词...
]


con=["/kaggle/input/shit123/训练数据/highQualityTrain.jsonl","/kaggle/input/shit123/训练数据/lowQualityTrain.jsonl","/kaggle/input/merging/merged123123214134134134113213123213123.jsonl"]
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score


# 假设你已经有一个特征向量 X 和对应的标签 Y
rf_classifier = RandomForestClassifier(n_estimators=100, random_state=42)
vectorizer = TfidfVectorizer(stop_words=stopwords,token_pattern='(?u)\\b\\w\\w+\\b')
total_list=[]
for l in range(0,3):
    with jsonlines.open(con[l], 'r') as reader:
            # 遍历每一行
        for line in reader:
            # 在这里可以修改每一行的值
            text="Question: "+line['Question']+" Answer: "+line['Answer']
            
            seg_list = jieba.lcut(text)

            total_list.append(" ".join(seg_list))
            # model=gensim.models.Word2Vec(filtered_seg_list, window=5, min_count=1, vector_size=128, workers=4,hs=1,negative=0)
        if(l==1):

            
            # print(total_list)
            X = vectorizer.fit_transform(total_list)
            # print(X)
            y_train1 =[0]*4986+[1] *4753 # 训练集标签
            rf_classifier.fit(X, y_train1)
            total_list=[]
        elif(l==2):
            # vectorizer = TfidfVectorizer()
            
            X = vectorizer.transform(total_list)
#             ytest1=[0]*524+[1]*495
            y_pred = rf_classifier.predict(X)
            for jj in range (1,len(y_pred)+1):
#                 print (y_pred[jj])
                if(y_pred[jj-1]==0):
                    dict[jj]+=1
            # 假设 y_true 是真实的标签，y_pred 是模型的预测标签
#             accuracy = accuracy_score(ytest1, y_pred)

#             print("预测准确率：", accuracy)





with jsonlines.open("3213.jsonl", 'a') as Writer:
    Writer.write(dict)











  ```
</details>

<br>
