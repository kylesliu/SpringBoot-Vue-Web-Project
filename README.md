# SpringBoot-Vue-Web-Project

基于 Spring Boot+Vue 的一个Web项目。利用 Nginx 反向代理来达成前后端分离。前端就是Vue，后端基于Spring Boot。

项目在Windows以及Linux上部署都已成功。80端口开放给Nginx，8080给Tomcat，在项目的CONF文件夹下给出了Linux和
Windows下nginx.conf文件的具体内容。Spring Boot集成了Tomcat，所以在Linux下是用了jar包（因为war坑比较多，
怂了= =）。

持久化框架使用 MyBatis，在 Spring Boot 下集成也比较方便，数据池使用阿里的 druid。

# 项目内容

因为没有画 UML 只能描述了。其实是实验室内部简单使用的工作管理，学生可以发布工作，可以参与工作（说白了就是交作
业= =），将完成的内容压缩成压缩包上传。并且可以任意下载，方便工作发起者检查。管理员登录后可以查看全部的工作信
息。学生能够看到当前进行中的工作，以及自己参与的工作。工作截止日期到了之后，也可以查看，类似历史工作。查看内容
会显示所有参加者的完成信息，例如：已完成、未完成、请假之类的，并且有简单的人数统计。
同时，参加者可以下载工作内容（允许借鉴他人作业）。“借鉴”我个人是提倡的，不看别人的代码，自己怎么能学到技术？

# 项目的已知缺点

当然整体是完成的，能够使用。只是希望以后实验室的学弟学妹能维护优化，我本身比较菜，瞎写写，很多东西写的不成体系
没有规范。虽然自称为是 REST 风格的，但是真的是么？这就靠大家来修改了。这里写一些我现在没有写的内容（比较懒。。）
以及我的一些想法：

1. 项目的前端完全没有碰。前端蛮重要的，我是一点渲染都没有，一点css都没写（index.html那一点点不算）。

2. 因为我本身不搞前端，所以写静态页还行，Vue 就算了，可以看到，我将 Vue 代码直接写在对应的 html 里面，因为我只会使用一点点，写一点 Ajax 罢了。这里需要真正搞前端的好好整理整理。
  
3. 安全性极差。这里是因为时间也不够充足，也是第一次尝试写，没有仔细研究安全性相关。思想还停留在前后端不分离的基础上。前端使用 URL 就能访问到一些不应该访问的页面，而禁止访问的方式仅仅是是使用 JavaScript 是不够的。后端虽然写了 Interceptor，但是因为路径问题，我自己禁用了。  
学弟学妹们可以看看 Spring Security 相关内容，看能不能解决这个问题。
  
4. session问题。不分离的时候，session的使用似乎是非常自然的，简单说：登录就可以用session。但是session跨域我没有去解决，所以只能前后端分开使用各自的 session，非常智障。简单百度了一些，似乎现在也不再使用 session，完全将后端当成 api，但是使用一种 token 的东西。可以研究一下。
  
5. 因为知道 war 包在部署上坑比较多，所以很怂的使用 jar 包了。如果比较懂 war 包部署，可以去 pom.xml 下改成 war。

6. 在 Linux 下使用 jar 包部署，说真的我个人不太喜欢，因为这样跟服务器上 tomcat 分开了。并且重启时还需要重新运行jar。不如 war 包更像“部署”。
  
# 关于服务器

不知道在实验室以后使用率怎么样，服务器是DO的，个人xx用的，并且DO的服务器大家都懂，延迟可能比较高。所以如果以后换服
务器了迁移可能是个问题。

# 关于疑问跟错误

当然还是可以喷的，哈哈，毕竟自己的问题，挨打要立正，当然仅限技术上。如果要维护，有不清楚的内容可以发邮件，提出问题
可以直接在 GitHub 上进行，也可以发邮件：1065077057@qq.com。QQ同上，只是不一定加。
