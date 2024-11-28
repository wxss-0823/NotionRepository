# Maven 教程

## 1. Maven 约定配置

| 目录                                 | 描述                                     |
| ------------------------------------ | ---------------------------------------- |
| `${basedir}`                         | 存放 pom.xml 和所有子目录                |
| `${basedir}/src/main/java`           | 项目的 java 源代码                       |
| `${basedir}/src/main/resources`      | 项目资源文件                             |
| `${basedir}/src/test/java`           | 项目的测试类                             |
| `${basedir}/src/test/resources`      | 项目的测试资源                           |
| `${basedir}/src/main/webapp/WEB-INF` | web 应用文件目录，web 项目的信息         |
| `${basedir}/target`                  | 打包输出目录                             |
| `${basedir}/target/classes`          | 编译输出目录                             |
| `${basedir}/target/test-classes`     | 测试编译输出目录                         |
| `Test.java`                          | Maven 只会自动运行符合该命名规则的测试类 |
| `~/.m2/repository`                   | Maven 默认的本地仓库目录位置             |

## 2. Maven POM

​	POM（Project Object Model，项目对象模型）是 Maven 工程的基本工作单元，是一个 XML 文件，包含了项目的基本信息，用于描述项目如何构建，声明项目依赖。

### 2.1. 必需字段

​	每个 POM 文件都需要 `project` 元素和三个必需字段：`groupId`，`artifactId`，`version`。

| 节点         | 描述                                 |
| ------------ | ------------------------------------ |
| `project`    | 工程的根标签                         |
| modelVersion | 模型版本需要设置为 4.0               |
| groupId      | 工程组的标识，在一个组织或项目中唯一 |
| artifactId   | 工程的标识，通常是工程的名称         |
| version      | 工程的版本号                         |

### 2.2. 依赖管理

​	POM 文件可以定义项目的依赖。

```xml
<dependecies>
	<dependency>
  	<groupId>org.springframework</groupId>
    <artifactId>spring-core</artifactId>
    <version>5.3.9</version>
  </dependency>
</dependecies>
```

### 2.3. 插件管理

​	POM 也可以定义构建过程中的插件。

```xml
<build>
	<plugins>
    <plugin>
    	<groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.8.1</version>
      <configuration>
      	<source>1.8</source>
        <target>1.8</target>
      </configuration>
    </plugin>
  </plugins>
</build>
```

### 2.4. 其他常用元素

#### 2.4.1. properties

​	用于定义项目中的一些属性变量。

```xml
<properties>
	<maven.compiler.source>1.8</maven.compiler.source>
  <maven.compiler.target>1.8</maven.compiler.target>
</properties>
```

#### 2.4.2. repositories

​	用于定义项目的依赖库。

```xml
<repositories>
	<repository>
  	<id>central</id>
    <url>https://repo.maven.apache.org/maven2</url>
  </repository>
</repositories>
```

#### 2.4.3. dependencyManagement

​	用于管理依赖的版本，特别是在多模块项目中。

```xml
<dependencyManagement>
	<dependencies>
  	<dependency>
    	<groupId>org.springframework</groupId>
      <artifactId>spring-core</artifactId>
      <version>5.3.9</version>
    </dependency>
  </dependencies>
</dependencyManagement>
```

#### 2.4.4. profiles

​	用于定义不同的构建配置，可以根据不同的环境进行构建。

```xml
<profiles>
	<profile>
  	<id>development</id>
    <properties>
    	<environment>dev</environment>
    </properties>
  </profile>
  <profile>
  	<id>production</id>
    <properties>
    	<environment>prod</environment>
    </properties>
  </profile>
</profiles>
```

#### 2.4.5. 继承和聚合

##### 继承

​	通过 `parent` 元素，一个 POM 文件可以继承另一个 POM 文件的配置。

```xml
<parent>
	<groupId>com.example</groupId>
  <artfactId>parent-project</artfactId>
  <version>1.0-SHAPSHOT</version>
</parent>
```

##### 聚合

​	通过 `modules` 元素，一个 POM 文件可以管理多个子模块。

```xml
<modules>
	<module>module1</module>
  <module>module2</module>
</modules>
```

### 2.5. Super POM

​	父（Super）POM 是 Maven 默认的 POM，所有 POM 都继承自一个父 POM。Maven 使用 `effective pom` （Super POM 加上工程自己的配置）来执行相关目标，它帮助开发者在 pom.xml 中尽可能少的配置，这些配置也可以被重写。

```shell
# 查看 Super POM 默认配置
mvn help:effective-pom
```

### 2.6. POM 标签大全

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0http://maven.apache.org/maven-v4_0_0.xsd">
	<!-- 父项目的坐标，没有规定则对应值为项目的默认值 -->
  <parent>
  	<!-- 被继承的父项目的构件标识符 -->
    <artifactId />
    <!-- 被继承的父项目的全球唯一标识符 -->
    <groupId />
    <!-- 被继承的父项目的版本 -->
    <version />
    <!-- 父项目的 pom.xml 文件的相对路径，默认为 ../pom.xml-->
    <!-- Maven 首先在构建当前项目的地方寻找父项，其次在文件系统的 relativePath 位置，然后在本地仓库，最后在远程仓库 -->
    <relativePath />
  </parent>
  <!-- 声明项目描述符遵循的 POM 模型版本 -->
  <modelVersion>4.0.0</modelVersion>
  <!-- 项目的全球唯一标识符，通常用全限定的包名区分，并且相对路径也由此生成 -->
  <groupId>asia.banseon</groupId>
  <!-- 构件的标识符，它和 groupId 一起唯一的标识一个构件，构件是项目产生或使用的一个东西，包括：JARs，源码， 二进制发布和 WARS 等 -->
  <artifactId>banseon-maven2</artifactId>
  <!-- 项目产生的构件类型 -->
  <packageing>jar</packageing>
  <!-- 项目当前版本，格式为：主版本.次版本.增量版本-限定版本号 -->
  <version>1.0-SHAPSHOT</version>
  <!-- 项目的名称，Maven 产生的文档用 -->
  <name>banseon-maven</name>
  <!-- 项目主页的URL，Maven 产生的文档用 -->
  <url>http://www.baidu.com/banseon</url>
  <!-- 项目的详细描述，Maven 产生的文档用 -->
  <description>A maven project to study maven.</description>
  <!-- 描述项目构建的前提条件 -->
  <prerequisites>
  	<!-- 构建该项目或使用该插件所需要的 Maven 最低版本 -->
    <maven />
  </prerequisites>
  <!-- 项目的问题管理系统 -->
  <issueManagement>
  	<!-- 问题管理系统的名字，例如：jira -->
    <system>jira</system>
    <!-- 该项目使用的问题管理系统的 URL -->
    <url>http://jira.baidu.com/banseon</url>
  </issueManagement>
  <!-- 项目持续集成信息 -->
  <ciManagement>
  	<!-- 持续集成系统的名字，例如：continuum -->
    <system />
    <!-- 该项目使用的持续集成系统的 URL -->
    <url />
    <!-- 构建完成时，需要通知的开发者/用户的配置项，包括：被通知者信息和通知条件 -->
    <notifiers>
    	<!-- 配置一种方式，当构建中断时，以该方式通知开发者/用户 -->
      <notifier>
      	<!-- 传送通知的途径 -->
        <type />
        <!-- 发生错误时是否通知 -->
        <sendOnError />
        <!-- 构建成功时是否通知 -->
        <sendOnSuccess />
        <!-- 发生警告时是否通知 -->
        <sendOnWarning />
        <!-- 通知发到哪里 -->
        <address />
        <!-- 扩展配置项 -->
        <configuration />
      </notifier>
    </notifiers>
  </ciManagement>
	<!-- 项目创建年份，4 位数字，产生版权信息时用 -->
  <inceptionYear />
  <!-- 项目相关邮件列表信息 -->
  <mailingLists>
  	<!-- 该元素描述了项目相关的一个邮件列表，自动产生的网站引用这些信息 -->
    <mailingList>
    	<!-- 邮件的名称 -->
      <name>Demo</name>
      <!-- 发送邮件的地址或链接 -->
      <post>banseon@123.com</post>
      <!-- 订阅邮件的地址或链接 -->
      <subscribe>banseon@126.com</subscribe>
      <!-- 取消订阅邮件的地址或链接 -->
      <unsubscribe>banseon@126.com</unsubscribe>
      <!-- 可以浏览邮件信息的 URL -->
      <archive>http:/hi.baidu.com/banseon/demo/dev/</archive>
    </mailingList>
  </mailingLists>
  <!-- 项目开发者列表 -->
  <developers>
  	<!-- 某个项目开发者的信息 -->
    <developer>
    	<!-- SCM 里项目开发者的唯一标识符 -->
      <id>HELLO WORLD</id>
      <!-- 项目开发者的全名 -->
      <name>banseon</name>
      <!-- 项目开发者的 E-mail -->
      <email>banseon@126.com</email>
      <!-- 项目开发者的主页 URL -->
      <url />
      <!-- 项目开发者在项目中扮演的角色 -->
      <roles>
      	<role>Project Manager</role>
        <role>Architect</role>
      </roles>
      <!-- 项目开发者所属组织 -->
      <organization>demo</organization>
      <!-- 项目开发者所属组织的 URL -->
      <organizationUrl>http://hi.baidu.com/banseon</organizationUrl>
      <!-- 项目开发者属性，如即时消息如何处理等 -->
      <properties>
      	<dept>No</dept>
      </properties>
      <!-- 项目开发者所在时区，-11 到 12 之间的整数 -->
      <timezone>-5</timezone>
    </developer>
  </developers>
	<!-- 项目的其他贡献者列表 -->
  <contributors>
  	<!-- 项目的其他贡献者，参见 developers/debeloper 元素 -->
    <contributor>
      <name />
      <email />
      <url />
      <organization />
      <roles />
      <timezone />
    	<properties />
    </contributor>
  </contributors>
	<!-- 项目的所有 License 列表，如果列出多个，用户可以选择一个，而不是接受全部 -->
  <licenses>
  	<!-- 描述项目的 License，用于生成项目的 web 站点的 license 页面 -->
    <license>
    	<!-- license 用于法律上的名称 -->
      <name>Apache 2</name>
      <!-- 官方的 license 正文页面的 URL -->
      <url>htpp://www.baidu.com/banseon/LICENSE-2.0.txt</url>
      <!-- 项目的分发方式：repo，可以从 Maven 库下载 manual，用户必须手动下载和安装依赖 -->
      <distribution>repo</distribution>
      <!-- 关于 license 的补充信息 -->
      <comments>A business-friendly OSS license.</comments>
    </license>
  </licenses>
	<!-- SCM(Source Control Management) 标签允许配置自己的代码库，供 Maven web 站点和其他插件使用 -->
  <scm>
  	<!-- SCM 的 URL，描述了版本库与版本库的连接方式，该连接只读 -->
    <connection>
    	scm:svn:http://svn.baidu.com/banseon/maven/banseon/banseon-maven2-trunk(dao-trunk)
    </connection>
    <!-- 开发者使用的连接，类似 connection 元素，该连接不仅仅可读 -->
    <developerConnection>
    	scm:svn:http://svn.baidu.com/banseon/maven/banseon/dao-trunk
    </developerConnection>
    <!-- 当前代码的标签，开发阶段默认为 HEAD -->
    <tag />
    <!-- 指向项目的可浏览 SCM 库的 URL，例如：ViewVC 或 Fisheye -->
    <url>http://svn:baidu.com/banseon</url>
  </scm>
  <!-- 描述项目所属组织的各种属性，Maven 产生的文档用 -->
  <organization>
  	<!-- 组织的全名 -->
    <name>demo</name>
    <!-- 组织主页的 URL -->
    <url>http://www.baidu.com/banseon</url>
  </organization>
  <!-- 构建项目需要的信息 -->
  <build>
  	<!-- 项目源码目录，该路径相对于 pom.xml 而言 -->
    <sourceDirectory />
    <!-- 项目脚本源码目录 -->
    <scriptSourceDirectory />
    <!-- 项目单元测试源码目录 -->
    <testSourceDirectory />
    <!-- 被编译过的应用程序 class 文件存放的目录 -->
    <outputDirectory />
    <!-- 被编译过的测试 class 文件存放的目录 -->
    <testOutputDirectory />
    <!-- 项目使用的一系列用于构建的扩展 -->
    <extensions>
    	<!-- 描述使用到的用于构建的扩展 -->
      <extension>
      	<!-- 用于构建的扩展的 groupId -->
        <groupId />
        <!-- 用于构建的扩展的 artifactId -->
        <artifactId />
        <!-- 构建扩展的版本 -->
        <version />
      </extension>
    </extensions>
    <!-- 当项目没有规定目标时的默认值 -->
    <defaultGoal />
    <!-- 描述了项目相关的所有资源路径列表，这些资源被包含在最终的打包文件里 -->
    <resources>
    	<!-- 项目相关或测试相关的资源路径 -->
      <resource>
      	<!-- 描述资源的目标路径，该路径相对于 target/classes 目录 -->
        <!-- 如果需要将资源放在特定的包里，需要设置元素值，如果只是把资源放在源码目录结构里，就不需要该配置 -->
        <targetPath />
        <!-- 列出保存项目参数值的文件 -->
        <filtering />
        <!-- 描述存放资源的目录，该路径相对于 POM 路径 -->
        <directory />
        <!-- 包含的模式列表，例如：**/*.xml -->
        <includes />
        <!-- 排除的模式列表，例如：**/*.xml -->
        <excludes />
      </resource>
    </resources>
    <!-- 单元测试相关的所有资源路径 -->
    <testResources>
    	<!-- 描述了测试相关的资源路径，参见 build/resources/resource 元素的说明 -->
      <testResource>
      	<targetPath />
        <filtering />
        <directory />
        <includes />
        <excludes />
      </testResource>
    </testResources>
    <!-- 构建产生的所有文件存放的目录 -->
    <directory />
    <!-- 产生的构件的文件名，默认是 ${artifactId}-${version} -->
    <finalName />
    <!-- 当 filtering 开关打开时，使用到的过滤器属性文件列表 -->
    <filters />
    <!-- 项目可以引用的默认插件信息 -->
    <!-- 该插件配置直到被引用时才会被解析或绑定到生命周期，给定插件的任何本地配置都会覆盖这里的配置 -->
    <pluginManagement>
    	<!-- 使用的插件列表 -->
      <plugins>
      	<!-- 描述每一个插件所需要的信息 -->
        <plugin>
        	<!-- 插件在仓库里的 groupId -->
          <groupId />
          <!-- 插件在仓库里的 artifactId -->
          <artifactId />
          <!-- 被使用的插件的版本或版本范围 -->
          <version />
          <!-- 是否从该插件下载 Maven 扩展，例如：打包、类型管理器 -->
          <extensions />
          <!-- 在构建的生命周期中执行一组目标的配置 -->
          <executions>
          	<!-- 插件执行需要的信息 -->
            <execution>
            	<!-- 执行目标的标识符，用于标识构建过程中的目标 -->
              <id />
              <!-- 绑定目标的构建生命周期 -->
              <phase />
              <!-- 配置的执行目标 -->
              <goals />
              <!-- 配置是否被传播到子 POM -->
              <inherited />
              <!-- 作为 DOM 对象的配置 -->
              <configuration />
            </execution>
          </executions>
          <!-- 项目引入插件所需的额外依赖 -->
          <dependencies>
          	<!-- 参见 dependencies/dependence 元素 -->
            <dependency>
            	...
            </dependency>
          </dependencies>
          <!-- 任何配置是否被传播到子项目 -->
          <inherited />
          <!-- 作为 DOM 对象的配置 -->
          <configuration />
        </plugin>
      </plugins>
    </pluginManagement>
    <!-- 使用的插件列表 -->
    <plugins>
    	<!-- 参见 build/pluginManagement/plugins/plugin 元素 -->
    	<pulugin>
      	<groupId />
        <artifactId />
        <version />
        <extensions />
        <executions>
        	<execution>
          	<id />
            <phase />
            <goals />
            <inherited />
            <configuration />
          </execution>
        </executions>
        <dependencies>
        	<!-- 参见 dependencies/dependency 元素 -->
          <dependency>
          	...
          </dependency>
        </dependencies>
        <goals />
        <inherited />
        <configuration />
      </pulugin>
    </plugins>
  </build>
  <!-- 配置与 POM 默认构建不同的设置 -->
  <profiles>
    <!-- 根据环境参数或命令行参数激活某个构建处理 -->
  	<profile>
      <!-- 构建配置的唯一标识符，用于命令行激活，也用于继承时合并具有相同标识符的 profile -->
      <id />
      <!-- 自动触发 profile 的条件逻辑 -->
      <!-- activation 是 profile 的开启钥匙，能够在特定的环境中自动使用特定的值，环境通过 activation 指定 -->
      <activation>
      	<!-- profile 默认是否激活的标志 -->
        <activeByDefault />
        <!-- 当匹配的 jdk 被检测到时，profile 被激活 -->
        <jdk />
        <!-- 当匹配的操作系统属性被检测到时，profile 被激活 -->
        <os>
        	<!-- 激活 profile 的操作系统的名字 -->
          <name>Windows XP</name>
          <!-- 激活 profile 的操作系统所属家族 -->
          <family>Windows</family>
          <!-- 激活 profile 的操作系统体系结构 -->
          <arch>x86</arch>
          <!-- 激活 profile 的操作系统的版本 -->
          <version>5.1.2600</version>
        </os>
        <property>
        	<!-- 激活 profile 的属性的名称 -->
          <name>mavenVersion</name>
          <!-- 激活 profile 的属性的值 -->
          <value>2.0.3</value>
        </property>
        <!-- 提供一个文件名，通过检测该文件存在或者不存在激活 profile -->
        <!-- missing 检测文件是否存在，不存在则激活 profile；exists 检查文件是否存在，存在则激活 profile -->
        <file>
        	<!-- 如果指定文件存在，则激活 profile -->
          <exists>/usr/local/hudson/hudson-home/jobs/maven-guide-zh-to-production/workspace/</exists>
          <missing>/usr/local/hudson/hudson-home/jobs/maven-guide-zh-to-production/worspace/</missing>
        </file>
      </activation>
      <!-- 与默认构建不同的项目构建信息，参见 build 元素 -->
      <build>
      	<defaultGoal />
        <resources>
        	<resource>
          	<targetPath />
            <filtering />
            <directory />
            <includes />
            <excludes />
          </resource>
        </resources>
        <testRources>
        	<testRource>
          	<targetPath />
            <filtering />
            <directory />
            <includes />
            <excludes />
          </testRource>
        </testRources>
        <directory />
        <finalName />
        <filters />
        <pluginManagement>
        	<plugins>
          	<!-- 参见 build/pluginManagement/plugins/plugin 元素 -->
            <plugin>
            	<groupId />
              <artifactId />
              <version />
              <extensions />
              <executions>
              	<execution>
                	<id />
                  <phase />
                  <goals />
                  <inherited />
                  <configuration />
                </execution>
              </executions>
              <dependencies>
              	<!-- 参见 dependencies/dependency 元素 -->
                <dependency>
                	...
                </dependency>
              </dependencies>
            </plugin>
          </plugins>
        </pluginManagement>
        <plugins>
        	<!-- 参见 build/pluginManagement/plugins/plugin 元素 -->
          <plugin>
          	<groupId />
            <artifactId />
            <version />
            <extensions />
            <executions>
            	<execution>
              	<id />
                <phase />
                <goals />
                <inherited />
                <configuration />
              </execution>
            </executions>
            <dependencies>
            	<!-- 参见 dependencies/dependency 元素 -->
              <dependency>
              	...
              </dependency>
            </dependencies>
            <goals />
            <inherited />
            <configuration />
          </plugin>
        </plugins>
      </build>
      <!-- 项目的模块，参见 modules -->
      <modules />
      <!-- 发现依赖和扩展的远程仓库列表 -->
      <repositories>
        <!-- 参见 repositories/repository 元素 -->
      	<repository>
        	<releases>
          	<enabled />
            <updatePolicy />
            <checksumPolicy />
          </releases>
          <snapshots>
          	<enabled />
            <updatePolicy />
            <checksumPolicy />
          </snapshots>
          <id />
          <name />
          <url />
          <layout />
        </repository>
      </repositories>
      <!-- 发现插件的远程仓库列表，用于构建和报表 -->
      <pluginRepositories>
      	<!-- 包含需要连接到远程插件仓库的信息，参见 repositories/repository 元素 -->
        <pluginRepository>
        	<releases>
          	<enabled />
            <updtePolicy />
            <checksumPolicy />
          </releases>
          <snapshots>
          	<enabled />
            <updatePolicy />
            <checksumPolicy />
          </snapshots>
          <id />
          <name />
          <url />
          <layout />
        </pluginRepository>
      </pluginRepositories>
      <!-- 描述了项目相关的所有依赖，并自动从项目定义的仓库中下载 -->
      <dependencies>
      	<!-- 参见 dependencies/dependency 元素 -->
        <dependency>
        	...
        </dependency>
      </dependencies>
      <!-- 不赞成使用，现在 Maven 忽略该元素 -->
      <reports />
      <!-- 项目使用报表插件产生报表的规范，参见 reporting 元素 -->
      <!-- 当用于执行 mvn site 时，这些报表就会运行 -->
      <reporting>
      	...
      </reporting>
      <!-- 参见 dependencyManagement 元素 -->
      <dependencyManagement>
      	<dependencies>
          <!-- 参见 dependencies/dependency 元素 -->
        	<dependency>
          	...
          </dependency>
        </dependencies>
      </dependencyManagement>
      <!-- 参见 distributionManagement 元素 -->
      <distributionManagement>
      	...
      </distributionManagement>
      <!-- 参见 properties 元素 -->
      <properties />
    </profile>
  </profiles>
  <!-- 模块被构建成项目的一部分，列出的每个模块元素是指向该模块目录的相对路径 -->
  <modules />
  <!-- 发现依赖和扩展的远程仓库列表 -->
  <repositories>
  	<!-- 包含需要连接到远程仓库的信息 -->
    <repository>
    	<!-- 配置远程仓库内发布版本的下载 -->
      <releases>
      	<!-- true 或 false 表示该仓库是否为下载某种类型构件开启 -->
        <enabled />
        <!-- 指定更新发生的频率，Maven 会比较本地 POM 与远程 POM 的时间戳 -->
        <!-- always：一直，daily：默认，每日，interval：X 分钟，never：永不 -->
        <updatePolicy />
        <!-- 指定当 Maven 验证构件校验文件失败时的行为 -->
        <!-- ignore：忽略，fail：失败，warn：警告 -->
        <checksumPolicy />
      </releases>
      <!-- 配置远程仓库内快照版本的下载 -->
      <!-- 利用 releases 和 snapshots 两组配置，POM 可以在每个单独的仓库中，为每种类型的构件采取不同的策略 -->
      <snapshots>
      	<enabled />
        <updatePolicy />
        <checksumPolicy />
      </snapshots>
      <!-- 远程仓库的唯一标识符，可用于匹配在 setting.xml 文件里配置的远程仓库 -->
      <id>banseon-repository-proxy</id>
      <!-- 远程仓库名称 -->
      <name>banseon-repository-proxy</name>
      <!-- 远程仓库 URL，按 protocal://hostname/path 的形式 -->
      <url>http://192.168.1.169:9999/repository/</url>
      <!-- 描述仓库布局类型，用于定位和排序构件 -->
      <!-- default：默认，legacy：遗留 -->
      <layout>default</layout>
    </repository>
  </repositories>
  <!-- 发现插件的远程仓库列表，插件用于构建和报表 -->
  <pluginRepositories>
  	<!-- 包含需要连接到远程插件仓库的信息，参见 repositoies/repository 元素 -->
    <pluginRepository>
    	...
    </pluginRepository>
  </pluginRepositories>
  <!-- 描述项目相关的所有依赖，这些依赖组成了项目构建过程中的一个个环节 -->
  <dependencies>
  	<dependency>
    	<!-- 依赖的 groupId -->
      <groupId>org.apache.maven</groupId>
      <!-- 依赖的 artifactId -->
      <artifactId>maven-artifact</artifactId>
      <!-- 依赖的版本号或版本范围 -->
      <version>3.8.1</version>
      <!-- 依赖的类型，默认为 jar，通常表示依赖文件的后缀名 -->
      <type>jar</type>
      <!-- 依赖的分类器，用于区分属于同一个 POM，但构建方式不同的构件 -->
      <classifier></classifier>
      <!-- 依赖的范围，在项目发布过程中，约定被包括的构件 -->
      <!-- compile：默认范围，用于编译，provided：类似于编译，用于支持 jdk 或容器，runtime：在执行时使用，test：用于 test 任务时使用，system：需要外在提供相应的元素，通过 systemPath 取得 -->
      <scope>test</scope>
      <!-- 仅供 system 范围使用，为依赖规定文件系统上的路径，需要绝对路径 -->
      <!-- 不鼓励使用，新版中可能被覆盖 -->
      <systemPath></systemPath>
      <!-- 当计算传递依赖时，从依赖构件的列表里，列出需要被排除的依赖构建集 -->
      <!-- 即告诉 Maven 只依赖项目，不依赖项目的依赖，用于解决版本冲突问题 -->
      <exclusions>
      	<exclusion>
        	<artifactId>spring-core</artifactId>
          <groupId>org.springframework</groupId>
        </exclusion>
      </exclusions>
      <!-- 描述可选依赖，可选依赖阻断依赖的传递性 -->
      <!-- 如果在项目 B 中把依赖 C 声明为可选依赖，那么依赖于 B 的项目 A 将无法传递依赖 C，需要在 A 中显式的引用对 C 的依赖 -->
      <optional>true</optional>
    </dependency>
  </dependencies>
  <!-- 不赞成使用，现在 Maven 忽略该元素 -->
  <reports></reports>
  <!-- 描述使用报表插件产生报表的规范 -->
  <reporting>
  	<!-- 描述是否包括默认的报表，ture：不包括默认的报表，包括项目信息中的报表 -->
    <excludeDefaults />
    <!-- 产生的报表的存放路径，默认为 ${project.build.directory}/site -->
    <outputDirectory />
    <!-- 使用的报表插件和它们的配置 -->
    <plugins>
      <!-- 描述报表插件需要的信息 -->
    	<plugin>
      	<!-- 报表插件在仓库里的 groupId -->
        <groupId />
        <!-- 报表插件在仓库里的 artifactId -->
        <artifactId />
        <!-- 报表插件的版本或版本范围 -->
        <version />
        <!-- 任何配置是否传播到子项目 -->
        <inherited />
        <!-- 报表插件的配置 -->
        <configuration />
        <!-- 用于为不同的报表集配置不同的规范 -->
        <reportSets>
        	<!-- 表示报表的一个集合，以及产生该集合的配置 -->
          <reportSet>
          	<!-- 报表集的唯一标识符，POM 继承时用到 -->
            <id />
            <!-- 同一报表集内，报表的配置 -->
            <configuration />
            <!-- 配置是否被继承到子 POMs -->
            <inherited />
            <!-- 集合内的报表列表 -->
            <reports />
          </reportSet>
        </reportSets>
      </plugin>
    </plugins>
  </reporting>
  <!-- 继承自该项目的所有子项目的默认依赖信息 -->
  <!-- 这部分依赖信息不会立即解析，仅当子项目声明一个依赖，包含 gourpId 与 artifactId 后，如果其他信息没有描述，则匹配到这里，并使用这里的默认依赖信息 -->
  <dependencyManagement>
  	<dependencies>
      <!-- 参见 dependencies/dependency 元素 -->
    	<dependency>
      	...
      </dependency>
    </dependencies>
  </dependencyManagement>
  <!-- 项目分发信息，在执行 mvn deploy 后表示要发布的位置 -->
  <distributionManagement>
  	<!-- 部署项目产生的构件到远程仓库需要的信息 -->
    <repository>
    	<!-- 分配给构件一个唯一的版本号，参见 repositories/repository 元素 -->
      <uniqueVersion />
      <id>banseon-maven2</id>
      <name>banseon maven2</name>
      <url>file://${basedir}/target/deploy</url>
      <layout />
    </repository>
    <!-- 配置构件的快照的部署地址，默认部署到 repository 元素配置的仓库 -->
    <!-- 参见 distributionManagement/repository 元素 -->
    <snapshotRepository>
    	<uniqueVersion />
      <id>banseon-maven2</id>
      <name>Baseon-maven2 Snapshot Repository</name>
      <url>scp://svn.baidu.com/banseon:/usr/local/maven-snapshot</url>
      <layout />
    </snapshotRepository>
    <!-- 部署项目的网站需要的信息 -->
    <site>
    	<!-- 部署位置的唯一标识符，用来匹配站点和 setting.xml 文件里的配置 -->
      <id>banseon-site</id>
      <!-- 部署位置的名称 -->
      <name>bussiness api website</name>
      <!-- 部署位置的 URL，按 protocol://hostname/path 的形式 -->
      <url>
      	scp://svn.baidu.com/banseon:var/www/localhost/banseon-web
      </url>
    </site>
    <!-- 项目下载页面的 URL，如果没有该元素，用户应该参考主页 -->
    <!-- 使用该元素可以帮助定位不在仓库中的构件 -->
    <downloadUrl />
    <!-- 用于重定向构件的信息 -->
    <relocation>
    	<!-- 构件新的 groupId -->
      <groupId />
      <!-- 构件新的 artifactId -->
      <artifacetId />
      <!-- 构件新的版本号或版本范围 -->
      <version />
      <!-- 显示给用户的，关于移动的额外信息，例如：原因 -->
      <message />
    </relocation>
    <!-- 给出构件在远程仓库的状态，不得在本地项目中设置该元素，因为工具会自动更新 -->
    <status />
  </distributionManagement>
  <!-- 以值代替名称，可以在整个 POM 中使用，也可以作为触发条件 -->
  <!-- 格式为 <name>value</name> -->
  <!-- 例如：在 activation 文件中配置触发条件为当属性 xxx 为 yyy，那么在此处配置属性为 <xxx>yyy</xxx> 即可触发 -->
  <properties />
</project>
```

## 3. Maven 构建生命周期

​	Maven 构建生命周期定义了一个项目构建跟发布的过程，一个典型的 Maven 构建（build）生命周期由以下几个阶段的序列组成。

| 阶段     | 处理     | 描述                                                   |
| -------- | -------- | ------------------------------------------------------ |
| validate | 验证项目 | 验证是否正确且所有必须信息是否是可用的                 |
| compile  | 执行编译 | 源代码编译在此阶段完成                                 |
| test     | 测试     | 使用适当的单元测试架构运行测试                         |
| package  | 打包     | 将编译后的代码打包成可分发的格式                       |
| verify   | 检查     | 对集成测试的结果进行检查，以保证质量达标               |
| install  | 安装     | 安装打包的项目到本地仓库，以供其他项目使用             |
| deploy   | 部署     | 拷贝最终的工程包到远程仓库，以共享给其他开发人员和工程 |

### 3.1. Clean 生命周期

​	删除目标目录中的编译输出文件。这通常是在构建之前执行，以确保项目从一个干净的状态开始。

- **pre-clean：**执行一些需要在 clean 之前完成的工作；
- **clean：**移除所有上一次构建生成的文件；
- **post-clean：**执行一些需要在 clean 之后立刻完成的工作。

**注意：**运行某个阶段的时候，它之前的所有阶段都会被运行。

### 3.2. Build 生命周期

​	也叫做 Default 生命周期，大体过程见上表。

#### 3.2.1. Build 生命周期阶段

| 生命周期阶段                                | 描述                                                         |
| :------------------------------------------ | :----------------------------------------------------------- |
| validate（校验）                            | 校验项目是否正确并且所有必要的信息可以完成项目的构建过程     |
| initialize（初始化）                        | 初始化构建状态，比如设置属性值                               |
| generate-sources（生成源代码）              | 生成包含在编译阶段中的任何源代码                             |
| process-sources（处理源代码）               | 处理源代码，比如说，过滤任意值                               |
| generate-resources（生成资源文件）          | 生成将会包含在项目包中的资源文件                             |
| process-resources （处理资源文件）          | 复制和处理资源到目标目录，为打包阶段最好准备                 |
| compile（编译）                             | 编译项目的源代码                                             |
| process-classes（处理类文件）               | 处理编译生成的文件，比如说对Java class文件做字节码改善优化   |
| generate-test-sources（生成测试源代码）     | 生成包含在编译阶段中的任何测试源代码                         |
| process-test-sources（处理测试源代码）      | 处理测试源代码，比如说，过滤任意值                           |
| generate-test-resources（生成测试资源文件） | 为测试创建资源文件                                           |
| process-test-resources（处理测试资源文件）  | 复制和处理测试资源到目标目录                                 |
| test-compile（编译测试源码）                | 编译测试源代码到测试目标目录                                 |
| process-test-classes（处理测试类文件）      | 处理测试源码编译生成的文件                                   |
| test（测试）                                | 使用合适的单元测试框架运行测试（Juint是其中之一）            |
| prepare-package（准备打包）                 | 在实际打包之前，执行任何的必要的操作为打包做准备             |
| package（打包）                             | 将编译后的代码打包成可分发格式的文件，比如JAR、WAR或者EAR文件 |
| pre-integration-test（集成测试前）          | 在执行集成测试前进行必要的动作。比如说，搭建需要的环境       |
| integration-test（集成测试）                | 处理和部署项目到可以运行集成测试环境中                       |
| post-integration-test（集成测试后）         | 在执行集成测试完成后进行必要的动作。比如说，清理集成测试环境 |
| verify （验证）                             | 运行任意的检查来验证项目包有效且达到质量标准                 |
| install（安装）                             | 安装项目包到本地仓库，这样项目包可以用作其他本地项目的依赖   |
| deploy（部署）                              | 将最终的项目包复制到远程仓库中与其他开发者和项目共享         |

**注意：**

- 当一个阶段通过 Maven 命令调用时，只有该阶段之前以及包括该阶段在内的所有阶段会被执行；
- 不同的 Maven 目标将根据打包的类型（JAR / WAR / EAR），被绑定到不同的 Maven 生命周期阶段。

#### 3.2.2. 插件目标

​	Build 生命周期由多个插件目标构成，一个插件目标代表一个作用于特定阶段的任务。一个构建阶段可以包含多个插件目标，有助于项目的构建和管理。每个插件目标可以被绑定到多个阶段，或者无绑定，不绑定到任何构建阶段的目标可以在构件生命周期之外通过直接调用执行。这些目标的执行顺序取决于调用目标和构建阶段的顺序。

### 3.3. Site 生命周期

- **pre-site：**执行一些需要在生成站点文档之前完成的工作；

- **site：**生成项目文档和站点信息；
- **post-site：**执行一些需要在生成站点文档之后完成的工作；

- **deploy-site：**将生成的站点信息发布到远程服务器。

## 4. Maven 构建配置文件

### 4.1. 构建配置文件的类型

| 类型                  | 路径                                                       |
| :-------------------- | :--------------------------------------------------------- |
| 项目级（Per Project） | 项目的 POM 文件 `pom.xml` 中                               |
| 用户级 （Per User）   | Maven 的设置 xml 文件 `%USER_HOME%/.m2/settings.xml` 中    |
| 全局（Global）        | Maven 全局的设置 xml 文件 `%M2_HOME%/conf/settings.xml` 中 |

### 4.2. 构建配置文件的激活

#### 4.2.1. 命令控制台

​	`profile` 可以定义一系列的配置信息，然后指定其**激活条件**。可以定义多个 `profile`，每个 `profile` 对应不同的激活条件和配置信息，从而达到不同环境使用不同配置信息的效果。

```xml
<profiles>
	<profile>
		<id>test</id>
			<build>
				...
			</build>
	</profile>
</profiles>
```

​	通过命令控制台，向 Maven 传递对应的参数，可以使用对应的配置。

```shell
mvn test -Ptest
```

- **test：**表示生命周期为 `test`；
- **-Ptest：**使用 `-P` 传递参数，参数为 `test`。

#### 4.2.2. setting.xml

​	打开 `%USER_HOME%/.m2` 目录下的 `settings.xml` 文件，如果 `setting.xml` 文件不存在就直接拷贝 `%M2_HOME%/conf/settings.xml` 到目录。

```xml
<settings xmlns="http://maven.apache.org/POM/4.0.0"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
   http://maven.apache.org/xsd/settings-1.0.0.xsd">
   ...
   <activeProfiles>
      <activeProfile>test</activeProfile>
   </activeProfiles>
</settings>
```

​	此时不需要传入参数也可以执行对应配置。

```shell
mvn test
```

#### 4.2.3. 环境变量

​	通过加入 `<activation>` 节点，设置激活条件的键值对。

```xml
<profiles>
	<profile>
		<id>test</id>
		<activation>
      <property>
        <name>env</name>
        <value>test</value>
      </property>
    </activation>
    <build>
			...
    </build>
  </profile>
</profiles>
```

​	当向 Maven 传递键值对为 `env=test` 时，执行对应配置，可以通过命令控制台。

```shell
mvn test -Denv=test
```

- **-Denv=test：**使用 `-D` 传递环境变量，`env` 是设置的 `<name>` 值，`test` 是设置的 `<value>` 值。

​	也可以通过加入 `<propertied>` 节点，固定调用一种配置。

```xml
<properties>
	<env>test</env>
</properties>
```

#### 4.2.4. 操作系统

​	可以设置触发条件为操作系统，当运行环境为对应的系统时，执行对应配置。

```xml
<profile>
   <id>test</id>
   <activation>
      <os>
         <name>Windows XP</name>
         <family>Windows</family>
         <arch>x86</arch>
         <version>5.1.2600</version>
      </os>
   </activation>
</profile>
```

#### 4.2.5. 文件判断

​	可以通过判断特定文件的存在或者缺失激活对应的配置文件。

```xml
<profile>
   <id>test</id>
   <activation>
      <file>
         <missing>target/generated-sources/axistools/wsdl2java/
         com/companyname/group</missing>
      </file>
   </activation>
</profile>
```

## 5. Maven 仓库

​	在 Maven 术语中，仓库是一个存放项目中以来的第三方库的位置（例如：`.m2` 路径）。在 Maven 中，任何一个依赖、插件或者项目构建的输出，都可以称之为构件。

### 5.1. 本地仓库

​	Maven 的本地仓库，在安装后并不会创建，它是在第一次执行 Maven 命令的时候才被创建。运行 Maven 的时候，Maven 所需要的任何构件都是直接从本地仓库获取的。如果本地仓库没有，它会首先尝试从远程仓库下载构件至本地仓库，然后再使用本地仓库的构件。

​	Windows 操作系统下，本地仓库的默认路径在 C 盘，可以通过在 Maven 安装目录下的 `setting.xml` 文件中自定义仓库路径。

```xml
<localRepository>[UserPath]</localRepository>
```

### 5.2. 中央仓库

​	Maven 中央仓库是由 Maven 社区提供的仓库，其中包含了绝大多数流行的开源 Java 构件，以及源码、作者信息、SCM、信息、许可证信息等。

- 这个仓库由 Maven 社区管理；
- 不需要配置；
- 需要通过网络才能访问。

​	Maven 社区提供了一个 URL 访问 [中央仓库](http://search.maven.org/#browse) ，简单的 Java 项目依赖的构件都可以在这里下载到。

### 5.3. 远程仓库

​	如果 Maven 在中央仓库中也找不到依赖的文件，它会停止构建过程并输出错误信息到控制台。为避免这种情况，Maven 提供了远程仓库的概念，它是开发人员自己定制仓库，包含了所需要的代码库或者其他工程中用到的 jar 文件。

```xml
<repositories>
	<repository>
		<id>companyname.lib</id>
		<url>http://download.companyname.org/maven2/lib</url>
  </repository>
</repositories>
```

### 5.4. 依赖搜索顺序

1. 首先在本地仓库中搜索，如果找不到，执行下一步；
2. 在中央仓库中搜索，如果找不到，并且有一个或多个远程库被设置，则执行第四步，如果找到了，则下载到本地仓库中备用；
3. 如果远程仓库没有被设置，Maven 将简单的停滞处理并抛出错误：无法找到依赖文件；
4. 在一个或多个远程仓库中搜索依赖的文件，如果找到了，则下载到本地仓库以备将来引用，否则 Maven 将停止处理并抛出错误。

## 6. Maven 插件

​	Maven 有三个标准的生命周期，每个生命周期都包含一系列的阶段（phase），这些 phase 相当于 Maven 提供的统一接口，其实现由 Maven 的插件完成。

​	例如，当输入命令 `mvn clean` 时，`clean` 对应于 Maven 的 Clean 生命周期，但是其具体操作是由 `maven-clean-plugin` 实现的。

```shell
# 实现插件的执行
mvn [plugin-name]:[goal-name]
```

### 6.1. 插件的类型

| 类型              | 描述                                                |
| ----------------- | --------------------------------------------------- |
| Build plugins     | 在构建时执行，并在 pom.xml 文件的元素中配置         |
| Reporting plugins | 在网站生成过程中执行，并在 pom.xml 文件的元素中配置 |

### 6.2. 常用的插件列表

| 插件     | 描述                                              |
| -------- | ------------------------------------------------- |
| clean    | 构建之后清理目标文件，删除目标目录                |
| compiler | 编译 Java 源文件                                  |
| surefile | 运行 JUnit 单元测试，创建测试报告                 |
| jar      | 从当前工程中构建 JAR 文件                         |
| war      | 从当前工程中构建 WAR 文件                         |
| javadoc  | 为工程生成 Javadoc                                |
| antrun   | 从构建过程的任意一个阶段中运行一个 ant 任务的集合 |

## 7. Maven 创建 Java 项目

### 7.1. 初始化 Java 应用项目

​	Maven 使用原型 `archetype` 插件创建项目，使用 `maven-archetype-quickstart` 创建简单的 Java 应用。

```shell
mvn archetype:generate "-DgroupId=com.companyname.bank" "-DartifactId=consumerBanking" "-DarchetypeArifactId=maven-artifactId-quickstart" "-DinteractiveMode=false"
```

### 7.2. 创建的目录树

```shell
.\---MVN
     \---consumerBanking
         |   pom.xml
         |   
         \---src
             +---main
             |   \---java
             |       \---com
             |           \---companyname
             |               \---bank
             \---test
                 \---java
                     \---com
                         \---companyname
                             \---bank
```

### 7.3. 文件结构说明

| 文件夹结构         | 描述                                     |
| ------------------ | ---------------------------------------- |
| consumerBanking    | 包含 src 文件夹和 pom.xml                |
| src/main/java      | Java 代码文件包含在 groupId 对应的目录下 |
| src/test/java      | 测试代码包含在 groupId 对应的目录下      |
| src/main/resources | 包含了图片/属性文件                      |

## 8. Maven 构建 & 测试项目

​	添加好源码文件与测试文件，并配置好 pom.xml 文件内容后，命令控制台执行：

```shell
mvn clean package
```

​	构建过程为：

1. Maven 清理目标目录；
2. Maven 编译源码文件，以及测试源码文件；
3. Maven 运行测试用例，测试编译完成的源码；
4. Maven 创建项目包；
5. 打包好的文件位于 `consumerBanking\target\classes` 下，名称为 `[artifactId]-[version].[packaging]` ；
6. 测试报告存放在 `comsumerBanking\target\surefile-reports` 文件中；

### 8.1. 添加多个源文件

​	通过 Java 的包声明，将一个项目的多个源文件声明为同一个包，包名对应于 `com.companyname.bank` ，Maven 会在打包时，自动识别同一个包下的源文件，并编译打包成一个输出文件。

## 9. Maven 引入外部依赖

​	如果项目需要引用第三方库的文件到项目，首先应该在 `consumerBanking\src` 路径下新建库文件夹 `lib`，并将文件复制进该路径；然后修改 pom.xml 文件中的依赖配置信息，通过系统路径引入依赖。

```xml
<dependencies>
	<dependency>
  	<groupId>ldapjdk</groupId>
    <artifactId>ldapjdk</artifactId>
    <version>1.0</version>
    <scope>system</scope>
    <systemPath>${basedir}\src\lib\ldapjdk.jar</systemPath>
  </dependency>
</dependencies>
```

## 10. Maven 项目文档

​	在 pom.xml 中添加文档相关的插件配置，以运行 `site` 命令。

```xml
<build>
	<pluginManagement>
  	<plugins>
    	<plugin>
      	<groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-site-plugin</artifactId>
        <version>3.3</version>
      </plugin>
      <plugin>
      	<groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-project-info-report-plugin</artifactId>
        <version>2.7</version>
      </plugin>
    </plugins>
  </pluginManagement>
</build>
```

​	在对应的项目文件夹下，执行 `mvn site` 命令，Maven 会自动生成项目文档。

### 10.1. 文件格式

​	Maven 使用一个名为 [Doxia](https://maven.apache.org/doxia/index.html) 的文档处理引擎来创建文档，它能将多种格式的源码读取成一种通用的文档模型。要为自定义的项目撰写文档，可以将内容写成以下几种常用的，可被 Doxia 转化的格式。

| 格式名 | 描述                     | 参考                                                      |
| ------ | ------------------------ | --------------------------------------------------------- |
| Apt    | 纯文本文档格式           | https://maven.apache.org/doxia/references/apt-format.html |
| Xdoc   | Maven 1.x 的一种文档格式 | https://jakarta.apache.org/site/jakarta-site2.html        |
| FML    | FAQ 文档适用             | https://maven.apache.org/doxia/references/fml-format.html |
| XHTML  | 可扩展的 HTML 文档       | https://en.wikipedia.org/wiki/XHTML                       |

## 11. Maven 快照

​	一个大型的软件应用通常包含多个模块，并且通常的场景是多个团队开发同一应用的不同模块。而不同团队的开发进度不同，如果一个团队近期正在进行快节奏的 bug 修复或者项目改进，那么他们可能每天都要发布一个版本到远程仓库，那么可能会发生：

- 该团队每次更新代码都需要告知其他团队；
- 其他团队需要经常修改 pom.xml 文件的配置至最新版本。

### 11.1. 快照的作用

​	鉴于上述发生的问题，Maven 提供了一种过渡版本控制方案，将经常需要修改的版本定义为快照（snapshot），例如：原始版本为 1.0，而快照版本为 1.0-SNAPSHOT，当某个团队需要经常更新版本时，每次上传覆盖上一次的快照版本即可，而对于其他团队而言，可以将版本设置为 1.0-SNAPSHOT，由于覆盖作用，Maven 每次构建时会自动获取最新的快照，直到该团队最终调试完成，将版本升级为 1.1，再修改正式的版本为 1.1 。

​	快照的情况下，Maven 会自动获取最新的快照，对于所有团队而言，调试期间均不需要修改版本号。但是也可以使用 `-U` 参数强制 Maven 下载最新的快照构建。

```shell
mvn clean package -U
```

## 12. Maven 自动化构建

​	自动化构建定义了这样一种场景：在一个项目成功构建后，依赖于其的相关工程即开始构建，这样可以保证其依赖项目的稳定。

**注意：**要保证当前项目和其他依赖工程的版本一致。

​	通过添加一个 `post-build` 目标来启动其他依赖工程。

```xml
<build>
	<plugins>
  	<plugin>
      <!-- 构建的时候执行插件 -->
    	<artifactId>maven-invoker-plugin</artifactId>
      <version>1.6</version>
      <configuration>
      	<debug>true</debug>
        <pomIncludes>
        	<pomInclude>xxx/pom.xml</pomInclude>
        	<pomInclude>yyy/pom.xml</pomInclude>
        </pomIncludes>
      </configuration>
      <executions>
      	<execution>
        	<id>build</id>
          <goals>
          	<goal>run</goal>
          </goals>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

## 13. Maven 依赖管理

​	Maven 一个核心的特性就是依赖管理，当处理多模块项目，项目间的依赖就变得非常复杂，管理也变得困难，针对此种情形，Maven 提供了一种高度控制的方法。

### 13.1. 可传递性依赖发现

​	Maven 可以避免去搜索所有嵌套的所需库的需求，可以通过读取项目的 `pom.xml` 文件，找出项目之间的依赖关系。使用者只需要在每个项目的 `pom.xml` 中定义好直接的依赖关系，其余的事情 Maven 会自动处理。

| 功能     | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| 依赖调节 | 决定当多个手动创建的版本同时出现时，被使用的依赖版本。如果两个依赖版本在依赖树的深度相同时，首先被声明的依赖将被使用 |
| 依赖管理 | 可以直接指定手动创建的某个版本供使用                         |
| 依赖范围 | 明确在构建过程每个阶段生效的依赖                             |
| 依赖排除 | 任何可以传递的依赖可以通过 `exclusion` 元素被排除在外，这样 Maven 不会将被排除的依赖加入项目 |
| 依赖可选 | 任何可以传递的依赖可以通过 `optional` 元素被标记为可选，可选会阻断依赖传递 |

### 13.2. 依赖范围

​	依赖范围就是依赖在构件过程中生效的阶段。

| 范围     | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| 编译阶段 | 表明依赖只在项目的类路径下有效，默认取值                     |
| 供应阶段 | 表明依赖由运行时的 JDK 或者网络服务器提供                    |
| 运行阶段 | 表明依赖在编译阶段不是必须的，但在执行阶段是必须的           |
| 测试阶段 | 表明依赖只在测试编译阶段和执行阶段                           |
| 系统阶段 | 表明需要通过绝对路径提供外部依赖                             |
| 导入阶段 | 表明依赖在一个 POM 中定义，并且，当前项目的依赖关系可以取代引用的 POM |

### 13.3. 依赖管理

​	通常情况下，在一个共通项目下有一系列项目，可以创建一个公共的依赖 POM 文件，作为一系列项目的父项目，该 POM 包含所有公共的依赖。

​	通过这种方式，子项目可以使用父项目的依赖，其他项目可以通过依赖子项目进而使用父项目的依赖，避免了依赖的重复定义。

## 14. Maven 自动化部署

​	为了防止不同团队之间的部署方案，时间，内容产生冲突，一种可行的自动化部署方案如下：

- 使用 Maven 构建和发布项目；
- 使用 SubVersion， 源码仓库来管理源代码；
- 使用远程仓库管理软件（Jfrog或者Nexus） 来管理项目二进制文件。

### 14.1. pom.xml 配置

- `scm`：配置 SVN 的路径，Maven 将从该路径将代码取下来；
- `repository`：构建的 WAR、EAR 或 JAR 文件的位置，或者其他源码构建成功后生成的构件的存储位置；
- `plugin`：配置 `maven-release-plugin` 插件来实现自动部署过程。

```xml
<scm>
  <url>http://www.svn.com</url>
  <connection>scm:svn:http://localhost:8080/svn/jrepo/trunk/
    Framework</connection>
  <developerConnection>scm:svn:${username}/${password}@localhost:8080:
    common_core_api:1101:code</developerConnection>
</scm>
<distributionManagement>
  <repository>
    <id>Core-API-Java-Release</id>
    <name>Release repository</name>
    <url>http://localhost:8081/nexus/content/repositories/Core-Api-Release</url>
  </repository>
</distributionManagement>
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-release-plugin</artifactId>
      <version>2.0-beta-9</version>
      <configuration>
        <useReleaseProfile>false</useReleaseProfile>
        <goals>deploy</goals>
        <scmCommentPrefix>[bus-core-api-release-checkin]-</scmCommentPrefix>	
     	</configuration>
    </plugin>
  </plugins>
</build>
```

### 14.2. Release 插件

​	Maven 使用 `maven-release-plugin` 插件完成以下任务。

```shell
# 清理工作空间，保证最新的发布进程成功运行
mvn release:clean
# 在上次发布不成功的情况下，回滚修改的工作空间代码和配置，保证发布过程成功进行
mvn release:rollback
# 完成一系列发布之前的准备工作，包括：检查本地是否存在未提交的修改；确保没有快照的依赖；改变应用程序的版本信息用以发布；更新 POM 文件到 SVN；运行测试用例；提交修改后的 POM 文件；为代码在 SVN 上做标记；增加版本号和附加快照以备将来发布；提交修改后的 POM 文件到 SVN 等
mvn release:prepare
# 切换代码到之前做标记的地方，运行 Maven 部署目标来部署 WAR 文件或构建相应的结构到仓库
mvn release:perform
```



































































































































































































































































































