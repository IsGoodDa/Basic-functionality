# 凯里市第十三小学“发展性评价”管理系统
”凯里十三小学生能力测评系统“，一个专为学生测试各项能力的平台；Carey 13 Primary Student Aptitude Assessment System", a platform designed for students to test various abilities.

## 前言

凯里十三小学能力测评系统是一款针对小学生开发的综合能力评估系统，旨在通过科学的测试和评估，为学生的学业发展和成长提供有益的指导和帮助。该系统通过多维度的测评方法，全面评估学生的学科知识、思维能力、语言表达、社交能力等方面的综合能力，为学生和家长提供科学的评估结果和优化建议。

（一）编写目的
编写本需求规格说明书的目的是为了详细呈现“发展性评价”管理系统的功能描述，以进一步定制开发的细节问题，便于与项目开发协调工作。本文档面向的读者主要是项目委托单位的管理人员、项目经理及项目组技术人员，希望能使本软件开发工作更明确、更具体。
（二）项目背景
本业务模型涉及的业务覆盖范围和组织覆盖范围。
1. 项目委托单位：凯里市第十三小学
2.开发单位：贵州电子信息职业技术学院信息与智能电子系
“发展性评价”管理系统项目是指利用新一代信息技术，以整合、系统的方式管理学生发展体系。中共中央、国务院发布的《关于全面加强新时代大中小学劳动教育的意见》指出，劳动教育是中国特色社会主义教育制度的重要内容，要紧密结合经济社会发展变化和学生生活实际，积极探索具有中国特色的劳动教育模式。

## 开发工具

凯里十三小学能力测评系统的开发使用了多种技术和工具，其中包括：

前端开发语言：HTML、CSS、JavaScript
后端开发语言：Java
数据库：MySQL
框架：Spring、Hibernate
工具：Eclipse、Tomcat、Sublime Text

## 功能模块

凯里十三小学能力测评系统具有以下主要功能模块：

- 基础功能：用户可以通过手机号、邮箱或第三方账号进行注册和登录。
- 班级管理：农民可以发布自己的农产品信息，包括名称、品种、产地、价格等信息。
- 评分管理：消费者可以搜索到自己需要的农产品信息，并下单购买。
- 广播管理：农民可以管理自己的订单，包括接受或拒绝订单、发货等操作。
- 评分审核：消费者可以进行支付，同时农民也可以进行提现。
- 评分生成：消费者可以对购买的农产品进行评价，以便提高购买体验和产品质量。

## 运行步骤

学生、教师、管理员等用户注册账号并登录系统。
学生进行测评测试，测试包括学科知识、思维能力、语言表达、社交能力等方面的综合能力。
系统根据测试结果，生成个性化的评估报告和学习建议，为学生和家长提供科学的指导和帮助。
教师使用系统进行学生测评，了解学生的学习情况和问题，并提供相应的教学建议。
学校管理层使用系统进行数据分析，了解学校教学水平和学生发展情况，为学校的管理和教学改进提供参考。

## 关于

凯里十三小学能力测评系统是由凯里市第十三小学开发的一款专业综合能力测评系统。该系统旨在通过科学、准确的测试和评估，为学生的学业发展和成长提供有益的指导和帮助。

# 用户信息管理
class User:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender

class UserManager:
    def __init__(self):
        self.users = []

    # 添加用户
    def add_user(self, name, age, gender):
        user = User(name, age, gender)
        self.users.append(user)

    # 查询用户
    def query_user(self, name):
        for user in self.users:
            if user.name == name:
                return user
        return None

    # 修改用户
    def modify_user(self, name, age=None, gender=None):
        user = self.query_user(name)
        if user:
            if age:
                user.age = age
            if gender:
                user.gender = gender

    # 删除用户
    def delete_user(self, name):
        user = self.query_user(name)
        if user:
            self.users.remove(user)
            
            
            
            
            
            <!DOCTYPE html>
<html>
<head>
	<title>My Information Page</title>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link rel="stylesheet" href="style.css">
</head>
<body>
	<header>
		<h1>My Information Page</h1>
	</header>
	<main>
		<section>
			<h2>About Me</h2>
			<p>Hello, my name is [name], and I am currently studying/working in [school/company name]. I love [hobbies/interests], and my goal is to [life goal/objective]</p>
		</section>
		<section>
			<h2>My Skills</h2>
			<ul>
				<li>Python programming</li>
				<li>Data analysis</li>
				<li>HTML/CSS coding</li>
			</ul>
		</section>
		<section>
			<h2>Contact Me</h2>
			<p>Email: [email address]</p>
			<p>Phone: [phone number]</p>
			<p>LinkedIn: [LinkedIn profile URL]</p>
		</section>
	</main>
	<footer>
		<p>Copyright © [year].
	</footer>
</body>
</html>






css
body {
	font-family: Arial, sans-serif;
	margin: 0;
	padding: 0;
	background-color: #F7F7F7;
	color: #333;
}

header {
	background-color: #196998;
	color: #FFF;
	padding: 20px;
}

main {
	margin: 20px;
}

section {
	margin-bottom: 40px;
}

h1, h2 {
	font-weight: normal;
}

li {
	margin-left: 20px;
}

a {
	color: #196998;
	text-decoration: none;
}

a:hover {
	color: #3A3A3A;
}

footer {
	background-color: #196998;
	color: #FFF;
	padding: 20px;
	text-align: center;
}


git add .
git commit -m "Add personal information"
git push origin master
