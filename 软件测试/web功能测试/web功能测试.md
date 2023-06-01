# Web功能测试

### 步骤

##### 1 安装浏览器插件

在`firefox`浏览器中安装`Katalon Recorder`插件

##### 2 使用插件进行录制

- 点击添加一个`Test Suites`
- 进行录制，在浏览器对需要测试的功能进行测试
- 若需要进行断言，点击选中要断言的部分，右键选择使用插件进行断言
- 操作完成后点击stop
- 点击Export，在Format中选择Java（WebDriver + Junit）格式的代码

##### 3 修改导出的代码，进行参数化测试

- 创建一个maven项目，导入依赖

pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>code</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-engine</artifactId>
            <version>5.5.2</version>
        </dependency>
        <dependency>
            <groupId>org.junit.platform</groupId>
            <artifactId>junit-platform-runner</artifactId>
            <version>1.5.2</version>
        </dependency>
        <!-- Parameterized Tests -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-params</artifactId>
            <version>5.5.2</version>
            <scope>test</scope>
        </dependency>
        <!-- selenium-java -->
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.8.1</version>
        </dependency>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-api</artifactId>
            <version>4.8.1</version>
        </dependency>
    </dependencies>
</project>
```

- 在Test中添加一个类，将导出的代码放入

- 由于导出的代码为Junit4的测试，我们导入的pom依赖是Junit5的，因此修改代码

- `@Before`以及`@After`修改为`@BeforeEach`以及`@AfterEach`，同时修改对应的代码

  

### 存在问题

##### 1 出现driver为空的报错

安装对应浏览器的驱动，这里使用的火狐浏览器的则安装`FirefoxDriver`的驱动

`geckodriver.exe`是火狐官方的驱动[下载路径](https://mirrors.huaweicloud.com/geckodriver/)

这里注意一定要和当前的浏览器版本对应，上网搜火狐浏览器与`geckodriver`对应的版本，否则会报错

选择win64版本

![geckodriver安装版本](https://github.com/BroMiaoY/Note/blob/main/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/web%E5%8A%9F%E8%83%BD%E6%B5%8B%E8%AF%95/geckodriver%E5%AE%89%E8%A3%85%E7%89%88%E6%9C%AC.png)

在测试代码中添加驱动路径：这里的地址是下载解压后的`geckodriver.exe`的本地地址。

```java
System.setProperty("webdriver.gecko.driver",
                   "D:\\study\\college\\software_testing\\geckodriver-v0.33.0-win64\\geckodriver.exe");
```

添加后代码：

```java
@Before
    public void setUp() throws Exception {
        System.setProperty("webdriver.gecko.driver",
                           "D:\\study\\college\\software_testing\\geckodriver-v0.33.0-win64\\geckodriver.exe");
        driver = new FirefoxDriver();
        baseUrl = "https://www.bing.com/";
        driver.manage().timeouts().implicitlyWait(60, TimeUnit.SECONDS);
        js = (JavascriptExecutor) driver;
    }

```

##### 2 元素被遮挡

出现报错

```
Element <tr class="el-descriptions-row"> could not be scrolled into view
```

出现该问题可能是页面的悬停菜单

这里的处理方式不太可取

直接在对应的报错行数上添加sleep函数

```java
Thread.sleep(1000)
```

