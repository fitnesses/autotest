# fitnesse
## jdbcslim
1. 项目地址 https://github.com/six42/jdbcslim
2. 可以直接在maven中下载jbdcslim的jar包
3. 使用方式参见 https://www.tomczhen.com/2016/01/21/continuous-integration-test-sqlserver-with-fitnesse/ 或者可以看他们的源码获取如何使用

## restfixture
1. 安装及使用方法见 https://testerhome.com/topics/1277
2. 项目地址 https://github.com/smartrics/RestFixture
3. rest关于http以及展示配置

    ```code
    |Table: Rest Fixture Config              |
    |http.client.connection.timeout     |5000|
    |restfixture.display.actual.on.right|true|
    ```

## 集成jenkins
1. 安装email ext plugin，注意配置邮件时，系统管理员邮件需与发件人一致
2. 安装fitnesse plugin，用来查看fitnesse执行结果的报表，具体配置参见https://wiki.jenkins.io/display/JENKINS/FitNesse+Plugin
3. 下载[fitnesse.jelly](https://gist.github.com/sergebug/9516308),并将其放到email-templates文件夹下
4. 项目配置中邮件类型选择，html，内容如下，可参考http://www.cnblogs.com/zz0412/p/jenkins_jj_01.html
    
    ```code
    ${JELLY_SCRIPT,template=”fitnesse”}
    ```
    


## 拾遗
1. import使用
    
    ```code
    |import                 |
    |six42.fitnesse.jdbcslim|
    ```
2. include页面
    
    ```code
    include SameLevelFile
    include <UpLevelFile.AutoTest
    ```
3. path定义
    
    ```code
    !define LibPath {/mnt/resource/work/workspace/fitnesse/plugins/}
    !path ${LibPath}jdbcslim/*.jar
    !path ${LibPath}jdbcfixture/*.jar
    !path ${LibPath}restfixture/*.jar
    ```
4. 变量定义
    
    ```code
    !define DATABASE_NAME {marketing_cloud}
    ```
5. 使用自定义的方法,需要引入对应的类，方法名中如果有多个参数，可以使用方法名进行分隔或者补空
    
    ```wiki
    |import               |
    |com.datatist.fitnesse|

    |script |Date Utils                                                          |
    |$start=|getStartOfTheDayWithPlusDays       |0|And Format|YYYY-MM-dd HH:mm:ss|
    |$end=  |getEndOfTheDayWithPlusDaysAndFormat|0|          |YYYY-MM-dd HH:mm:ss|
    ```
    
6. 

