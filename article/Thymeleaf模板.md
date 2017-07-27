# article
# Thymeleaf模板引擎
- Thymeleaf是一个XML/XHTML/HTML5模板引擎，可用于Web与非Web环境中的应用开发。它是一个开源的Java库，基于Apache License 2.0许可，由Daniel Fernández创建，该作者还是Java加密库Jasypt的作者。
- \#代表 获取对象 从 messages bundle 也就是消息的资源本地化文件
- \$表示从model里面获取

---

# 下面介绍常用的标签

`th:fragment="public"` 相当于 include标签
`th:each="user : ${users}"` 相当于c:foreach  使用时候
如上面
```html
<tr th:each="user : ${users}">
	<td th:text="${user.id}">001</td>
	<td th:text="${user.name}">张三</td>
	<td th:text="${user.xx}">java</td>
	<td th:text="${user.xx}">程序员</td>
</tr>
```

## 超链接动态化
- `th:href="@{/user/delete(id=${u.id})}"`
## 表达式基本对象：
- `#ctx`：context object
- `#root`或者`#vars`
- `#locale`
- `#httpServletRequest`
- `#httpSession`
## 表达式功能对象：
- `#dates`：java.util.Date的功能方法类。
- `#calendars`:类似#dates，面向java.util.Calendar
- `#numbers`:格式化数字的功能方法类。
- `#strings`：字符串对象的功能类，
- contains,startWiths,prepending/appending等等。
- `#objects`:对objects的功能类操作。
- `#bools`:对布尔值求值的功能方法。
- `#arrays`：对数组的功能类方法。
- `#lists`:对lists功能类方法
- `#sets`
- `#maps`
- `#aggregates`:对数组或者集合创建聚合的功能方法，
-  `th:text="${#aggregates.sum(o.orderLines.{purchasePrice * amount})}"`
- `#messages`:在变量表达式中获取外部信息的功能类方法。
- `#ids`：处理可能重复的id属性的功能类方法。
## Form表单提交
```html
<form action="#" th:action="@{/users/add}" th:object="${myuser}" method="post">
```
这里`th：Object`表示表单与 该`myuser`注入的实体映射，
在表单 `th:field="*{id}` 则表示 该表单的值 与` myuser`的`id`绑定 
`th:remove="all"`  使用了该标签 将在运行时候移除所有的元素
## 判断条件
```html
<td class="status" th:if="${#strings.isEmpty(status)}" th:text="这状态为空">这里显示状态不为空</td>

${not #strings.isEmpty(status)}
```

---
## 数字格式与日期格式 
```html
<dd th:text="${#numbers.formatDecimal(product.price, 1, 2)}">180</dd>

<dd th:text="${#dates.format(product.availableFrom, 'yyyy-MM-dd')}">2014-12-01</dd>

<dd th:text="${'$'+product.price}">235</dd>
```
