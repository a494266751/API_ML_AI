## 产品需求
| 发布日期 | 11/25/2018 |
| --------   | -----:  |
| 史诗 | 动物之家 | 
| 文件状态 | 进行中 | 
| 文件主人 | 蔡俊钦 | 
| 领头的设计师  | 蔡俊钦 | 
| 领头的开发者  | 蔡俊钦 | 
| 领头的测试者  | 蔡俊钦 | 

## 目标（加值宣言）
> * 该产品是一个科普类与电商类结合的产品，运用推荐系统，智能地为用户推荐感兴趣的内容及商品。
> * 该产品运用百度-动物识别API，用户只需拍照即可得到眼前动物的相关信息，为野外出行、探险的用户提供更多乐趣。
> * 该产品也是为了打开儿童教育的领域，孩子的家长们可以使用此产品动物识别的智能拍照，寓教于乐，帮助孩子们成长。
> * 市面上缺少科普类的产品，也缺少科普与电商相结合的模式的产品，更缺少动物识别拍照获取动物信息，从而进行科普的产品。我相信此产品在市场上会有很大的优势。

## 背景和战略契合处（核心价值）
  我做这个产品的原因是此产品有趣且有意义，对拓展人的眼界和保护大自然都有很大作用。该产品采用AI智能，如推荐系统、图像识别，这也反映该产品的核心价值与功能，我们要使用这两项AI智能，为用户提供科普、满足用户的购物欲望，也可寓教于乐。这也符合AI人工智能、保护大自然等时代大环境。

## 假设
> * 该产品是一个手机端的产品，支持手机的Ios及Android系统。
> * 产品功能完善，是电商类APP与科普类APP的结合。

## 人工智能概率性
  在图像识别及推荐系统上难免出现失败情况，在拍照进行动物识别阶段失败时，则给用户诙谐、幽默的错误反馈或是推荐类似的内容。

## 需求列表
| # | 标题 | 用户案例 | 重要程度 | 笔记 |
| --------   | -----| ----  |--------   |-----:  |
| 1 | 识别功能 | 用户拍摄或加载相册中动物的相片，产品就能调用百度-动物识别API，智能地识别并展示出相应的动物资料及科普知识 | 极其重要 | 核心功能，要准确，对手机的相机要求高 |
| 2 | 科普 | 用户进入科普的界面，会展示出推荐系统筛选的各类、各种及各样的动物资料  | 极其重要 | 核心功能，推荐系统智能筛选内容，也适合小孩子使用该产品 |
| 3 | 商城 | 用户进入商城的界面，会展示出推荐系统筛选的各类动物的食物及相关饰物、玩偶等等商品  | 重要 | 推荐系统智能筛选商品，可以增加收入，篇幅不易过多 |
 
## 使用者交互及设计
  ![qidong](https://github.com/a494266751/API_ML_AI/blob/master/img/qidong.png)  
  ![首页](https://github.com/a494266751/API_ML_AI/blob/master/img/shouye.png)
  ![科普页](https://github.com/a494266751/API_ML_AI/blob/master/img/kepu.png) 
  ![拍照页](https://github.com/a494266751/API_ML_AI/blob/master/img/paizhao.png)
  ![相片结果页](https://github.com/a494266751/API_ML_AI/blob/master/img/jieguo.png) 
  ![商城页](https://github.com/a494266751/API_ML_AI/blob/master/img/shangchen.png)
  ![个人中心页](https://github.com/a494266751/API_ML_AI/blob/master/img/gerenzhongxin.png)
  
## 调用-百度动物识别API（Python）----与阿里云动物识别API相比，它是市面上较为成熟、性价比高、风险最低的API，且在未来很长一段时间也不会被淘汰。
```python
# encoding:utf-8
import base64
import urllib
import urllib2

'''
动物识别
'''

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v1/animal"

# 二进制方式打开图片文件
f = open('[本地文件]', 'rb')
img = base64.b64encode(f.read())

params = {"image":img,"top_num":6}
params = urllib.urlencode(params)

access_token = '[调用鉴权接口获取的token]'
request_url = request_url + "?access_token=" + access_token
request = urllib2.Request(url=request_url, data=params)
request.add_header('Content-Type', 'application/x-www-form-urlencoded')
response = urllib2.urlopen(request)
content = response.read()
if content:
    print content
```

## 问题（用户痛点）
| 问题 | 结果 |
| --------   | -----:  |
| 用户想要快速知道眼前的动物叫什么？是什么品种？ | 拍照上传至本产品，通过百度-动物识别API，即能查到该动物的详细信息 | 
| 用户是位母亲，想要教两岁的孩子学习，但又不想用传统枯燥的方法，该如何？ | 该产品提供科普界面，且由推荐系统通过历史记录智能筛选您可能感兴趣的内容，界面上提供配图，小孩子看起来也不会觉得枯燥 | 
| 用户想要在了解科普知识的同时购买XX动物相关的食物、玩偶等，该如何？ | 该产品提供商城页面。且由智能系统智能筛选您可能感兴趣的商品，方便用户购买 | 

## 不做
> * 目前阶段只做好动物识别相关的功能，不做其他物品识别。
> * 不做浪费体积的附加功能、界面，保证产品占内存最小化。
> * 暂时不做除手机以外的设备。

## 最小可行性产品
  目前的最小可行性产品就是做到此PRD所表述的介绍及功能。
 
## 不足
  该产品会存在科普界面数据不完善、未做好社交功能以及界面设计不够简洁等不足，但本项目运用百度-动物识别API、推荐系统，以突显人工智能解决问题的方法，增进用户的体验。
