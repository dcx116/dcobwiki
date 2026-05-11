### 方式一：使用-p参数

```
docker-compose -p myproject up -d`
```

这样生成的容器名称就会是myproject_web_1和myproject_db_1。

### 方式二：设置环境变量

```
export COMPOSE_PROJECT_NAME=myproject
docker-compose up -d
```
