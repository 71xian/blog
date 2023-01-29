# maven笔记

maven 生命周期

clean

validate

compile

test

package

verify

install

site

deploy

依赖管理

```xml
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>${spring-cloud.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>com.alibaba.cloud</groupId>
                <artifactId>spring-cloud-alibaba-dependencies</artifactId>
                <version>${spring-cloud-alibaba.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>com.squareup.okhttp3</groupId>
                <artifactId>okhttp</artifactId>
                <version>4.10.0</version>
                <scope>compile</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
```

路径优先  上面的okhttp覆盖了springboot里的okhttp

当前依赖产生依赖冲突  谁先定义就用谁

父依赖和子依赖冲突 优先使用子依赖

上传到私服  codeup有教程