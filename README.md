# check-style-maven-example

CheckStyle Maven插件的使用实例.

## 1.配置

1.1 复制本项目的checkstyle.xml到需要使用CheckStyle的Maven项目根目录.
1.2 配置需要使用CheckStyle的Java项目的pom.xml
1.2.1 手动检查配置如下

```
<project>
    ....
    <build>
        ...
        <plugins>
            ...
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-checkstyle-plugin</artifactId>
                <version>2.17</version>
                <configuration>
                    <configLocation>checkstyle.xml</configLocation>
                    <encoding>UTF-8</encoding>
                    <consoleOutput>true</consoleOutput>
                    <failsOnError>true</failsOnError>
                </configuration>
            </plugin>
            ...
        </plugins>
        ...
    </build>
    ...
</project>
```

1.2.2 自动检查配置如下

```
<project>
    ....
    <build>
        ...
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-checkstyle-plugin</artifactId>
                <version>2.17</version>
                <configuration>
                    <configLocation>checkstyle.xml</configLocation>
                    <encoding>UTF-8</encoding>
                    <consoleOutput>true</consoleOutput>
                    <failsOnError>true</failsOnError>
                </configuration>
                <executions>
                    <execution>
                        <id>validate</id>
                        <phase>validate</phase>
                        <goals>
                            <goal>check</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        ...
    </build>
    ...
</project>
```

## 2.检查

2.1 手动检查 使用`maven checkstyle:check`命令执行手动检查.

2.2 自动检查会在maven执行validate的时候自动执行.

## 3.主要检查项目

3.1 每行代码长度不超过100字符.

3.2 public方法需要写注释.

3.3 代码文件统一UTF-8编码.

3.4 包,类,方法,属性名规范检查.

3.5 空catch块检查.