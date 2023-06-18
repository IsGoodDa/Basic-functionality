### 以下是Java代码示例：

### Here is a Java code example:

// 学生类

public class Student {

    private String id;
    
    private String name;
    
    private String gender;
    
    private int age;

    // 构造函数
    public Student(String id, String name, String gender, int age) {
        this.id = id;
        this.name = name;
        this.gender = gender;
        this.age = age;
    }

    // Getter 和 Setter 方法
    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getGender() {
        return gender;
    }

    public void setGender(String gender) {
        this.gender = gender;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

// 评价记录类
public class EvaluationRecord {
    private String studentId;
    private String evaluator;
    private String content;
    private Date evaluationTime;

    // 构造函数
    public EvaluationRecord(String studentId, String evaluator, String content, Date evaluationTime) {
        this.studentId = studentId;
        this.evaluator = evaluator;
        this.content = content;
        this.evaluationTime = evaluationTime;
    }

    // Getter 和 Setter 方法
    public String getStudentId() {
        return studentId;
    }

    public void setStudentId(String studentId) {
        this.studentId = studentId;
    }

    public String getEvaluator() {
        return evaluator;
    }

    public void setEvaluator(String evaluator) {
        this.evaluator = evaluator;
    }

    public String getContent() {
        return content;
    }

    public void setContent(String content) {
        this.content = content;
    }

    public Date getEvaluationTime() {
        return evaluationTime;
    }

    public void setEvaluationTime(Date evaluationTime) {
        this.evaluationTime = evaluationTime;
    }
}



<!DOCTYPE html>
<html>
<head>
  <title>我的 Github 页面</title>
  <link href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700" rel="stylesheet">
  <style>
    body {
      background-color: #f7f7f7;
      font-family: 'Roboto', sans-serif;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #ffffff;
      border-bottom: 1px solid #eeeeee;
      display: flex;
      justify-content: space-between;
      padding: 20px;
    }

    .logo {
      font-size: 24px;
      font-weight: 700;
    }

    nav a {
      color: #333333;
      font-weight: 500;
      margin-left: 20px;
      text-decoration: none;
    }

    h1 {
      font-size: 48px;
      font-weight: 700;
      margin: 0 auto;
      max-width: 800px;
      padding: 80px 20px;
      text-align: center;
    }

    footer {
      background-color: #333333;
      color: #ffffff;
      font-size: 14px;
      padding: 20px;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">My Github Page</div>
    <nav>
      <a href="#">Home</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </nav>
  </header>
  <h1>Welcome to My Github Page</h1>
  <footer>&copy; 2023 My Github Page. All rights reserved.</footer>
</body>
</html>
