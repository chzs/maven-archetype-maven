# maven-archetype-maven
以下讲解了如何自己构建一个简单的Maven Archetype的过程，本此实践参考许晓斌的《Maven实战》一书 以及 互联网上搜索的一些知识。

## 1.Archetype 项目的实现
如maven-archetype-maven里的代码所示，其主要包括以下几个东西：  
  (1) pom.xml -- 项目根目录下的pom.xml文件  
  (2) src/main/resources/archetype-resources/pom.xml -- 基于此Archetype生成项目的pom.xml原型  
  (3) src/main/resources/META-INF/maven/archetype-metadata.xml -- 项目定义文件，此文件决定了生成项目的结构和内容  
  (4) src/main/resources/archetype-resources/* -- 一些原始类，原始配置文件  

下面有两种方式：
    1.在实现上面代码的编写之后，执行 *mvn clean install* 生成jar包并安装到本地repository库中
    2.如果packaging设置为'maven-archetype',那么需要在pom.xml文件中添加插件：maven-archetype-plugin,并在extensions中添加archetype-packing包
上面的第二种方法



## 2.创建本地archetype-catalog.xml文件
1. 使用 * mvn archetype:crawl -Drepository= -DarchetypeCatalog= * 生成本地archetype-catalog.xml文件
2. 若使用maven-archetype-plugin插件，那么使用 mvn archetype:jar命令

## 3.创建新项目
使用 * mvn archetype:generate -DarchetypeCatalog=local * 会加载生成在repository的archetype-catalog.xml文件，之后按普通的创建流程走就行。
