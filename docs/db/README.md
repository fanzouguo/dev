# 数据库规范

## tmind-dbProvider
The db provider base class for tFrameV9 of shanghai smpoo soft comoration.

### 前端标准 CRUD 请求参数

* #### 查询
```js
{
	// 查询参数无需申明 tblName，而是取决于路由参数
	payload: {	// payload 中的参数会直接被解析为 SELECT SQL语句的 where 条件
		foo: 'bar' | bar | ['bar'] | [bar]
	}
}

// ----------------- 或着 -----------------

{
	// 查询参数无需申明 tblName，而是取决于路由参数
	payload: [	// payload 中的参数会直接被解析为 SELECT SQL语句的 where 条件
		{
			foo: 'bar' | bar | ['bar'] | [bar]
		},
		{
			foo: 'bar' | bar | ['bar'] | [bar]
		}
	]
}
```

* #### 新增
> 单表
```js
{
	// 单表参数无需申明 tblName，而是取决于路由参数
	payload: {
		foo: 'bar'
		bar: foo
	}
}
// ----------------- 或着 -----------------
{
	// 单表参数无需申明 tblName，而是取决于路由参数
	payload: [
		{
			foo: 'bar'
			bar: foo
		},
		{
			foo: 'bar'
			bar: foo
		}
	]
}
```

> 主从表新增
```js
{
	// 主表参数无需申明 tblName，而是取决于路由参数
	payload: [
		{
			foo: 'bar'
			bar: foo
		},
		{
			foo: 'bar'
			bar: foo
		}
	],
	detail: [
		{
			tblName: 'xxx',	// 明细表名称
			payload: {
				foo: 'bar'
				bar: foo
			}
		}
	]
}
```

* #### 修改
> 单表
```js
{
	// 单表参数无需申明 tblName，而是取决于路由参数
	payload: {
		id: x,	// 必须存在ID键值
		foo: 'bar'
		bar: foo
	}
}
```

> 主从表
```js
{
	// 主单表参数无需申明 tblName，而是取决于路由参数
	payload: {
		id: x,	// 必须存在ID键值
		foo: 'bar'
		bar: foo
	},
	// 明细表参数集合
	detail: {
		tblName: '...',	// 明细表名称
		payload: {
			foo: 'bar'
			bar: foo
		}
	}
}
// ----------------- 或着 -----------------
{
	// 主表参数无需申明 tblName，而是取决于路由参数
	payload: {
		id: x,	// 必须存在ID键值
		foo: 'bar'
		bar: foo
	},
	// 明细表参数集合
	detail: [
		{
			tblName: '...',	// 明细表名称
			payload: {
				foo: 'bar'
				bar: foo
			}
		},
		{
			tblName: '...',	// 明细表名称
			payload: {
				foo: 'bar'
				bar: foo
			}
		}
	]
}
```

* #### 删除
> 单表
```js
{
	// 单表参数无需申明 tblName，而是取决于路由参数
	paylod: {	// payload 中的参数会直接被解析为 DELETE SQL语句的 where 条件
		id: x,	// 必须存在ID键值
	}
}

// ----------------- 或着 -----------------
{
	// 单表参数无需申明 tblName，而是取决于路由参数
	payload: [	// payload 中的参数会直接被解析为 DELETE SQL语句的 where 条件
		{
			id: x
		},
		{
			code: 'foo'
		}
	]
}
```

> 主从表
```js
{
	// 主表参数无需申明 tblName，而是取决于路由参数
	payload: {	// payload 中的参数会直接被解析为 DELETE SQL语句的 where 条件
		id: x,	// 主表参数必须存在ID键值
	},
	detail: [
		{
			tblName: '...',	// 明细表名称
			payload: {	// payload 中的参数会直接被解析为 DELETE SQL语句的 where 条件
				foo: 'bar'
				x: y
			}
		}
	]
}
```

### WHERE 条件构造器

#### 说明

* 以 keyValue 形式表示 SQL 语句中的 WHERE 条件部分的最小比较单元，如：
``` javascript
{
	id: 1
}
// 代表
id = 1
```

#### 用例

* 传入代表 where 条件中，不含 WHERE 关键词的字符串部分
``` sql
id = 1 and name = 'foo'
```

* 传入键值对形式的 JSON 对象
``` sql
{
	id: 1
	gt$code: 2
	between$data: ['2021-01-01', '2021-08-01']
}
```

* 传入数组，数组元素是键值对形式的 JSON 对象
``` sql
[
	{
		id: 1
	},
	{
		name: 'foo'
	}
]
```

#### 结构

> AND： JSON 对象中的各个键值之间，以 AND 连接
``` javascript
{
	id: 1,
	name: 'aaa'
}
// 代表
id = 1 AND name = 'aaa'
```


> OR：数组元素间，以 OR 连接
``` javascript
[
	{
		id: 1,
		name: 'aaa'
	},
	{
		name: 'bbb'
	}
]
// 代表
(id = 1 AND name = 'aaa') OR (name = 'bbb')
```

### 谓词

> =（等于）：键值对即代表 键 = 值，或者以“字段名”作为键，但附加 $ 为前缀时，键值关系也解析为“等于”
``` javascript
{
	id: 1
}
// 代表
id = 1
// 或则
{
	$id: 1
}
// 代表
id = 1
```

> <>（不等于）：以“字段名”作为键，但附加 _$ 为前缀时，键值关系解析为“不等于”
``` javascript
{
	'_$id': 1
}
// 代表
id <> 1
```

> >（大于）：以“字段名”作为键，但附加 gt$ 为前缀时，键值关系解析为“大于”
``` javascript
{
	gt$id: 1
}
// 代表
id > 1
```

> <（小于）：以“字段名”作为键，但附加 lt$ 为前缀时，键值关系解析为“小于”
``` javascript
{
	lt$id: 1
}
// 代表
id < 1
```

> >=（大于等于）：以“字段名”作为键，但附加 gte$ 为前缀时，键值关系解析为“大于等于”
``` javascript
{
	gte$id: 1
}
// 代表
id = 1
```

> <=（小于等于）：以“字段名”作为键，但附加 lte$ 为前缀时，键值关系解析为“小于等于”
``` javascript
{
	lte$id: 1
}
// 代表
id = 1
```

> BETWEEN（介于）：以“字段名”作为键，但附加 between$ 为前缀时，键值关系解析为“介于”
``` javascript
{
	between$date: ['2021-01-01', '2021-02-01']
}
// 代表
date BETWEEN '2021-01-01' AND '2021-02-01'
```

> BETWEEN（非介于）：以“字段名”作为键，但附加 _between$ 为前缀时，键值关系解析为“非介于”
``` javascript
{
	_between$date: ['2021-01-01', '2021-02-01']
}
// 代表
date NOT BETWEEN '2021-01-01' AND '2021-02-01'
```

> IN（限于）：当键值的值为数组时，键值关系解析为“介于”
``` javascript
{
	id: [1, 2, 3]
}
// 代表
id IN (1, 2, 3)
```

> NOT IN（排除）：以“字段名”作为键，但附加 _$ 为前缀时，且值为数组时，键值关系解析为“排除”
``` javascript
{
	_$id: [1, 2, 3]
}
// 代表
id NOT IN (1, 2, 3)
```

> LIKE（类似于）：以“字段名”作为键，但附加 like$ 为前缀时，其值键值关系解析为“类似于”
``` javascript
{
	like$id: 'foo'
}
// 代表
id LIKE '%foo%'
```

> LIKE（开头类似于）：以“字段名”作为键，但附加 like1$ 为前缀时，其值键值关系解析为“类似于”
``` javascript
{
	like1$id: 'foo'
}
// 代表
id LIKE 'foo%'
```

> LIKE（结尾类似于）：以“字段名”作为键，但附加 like2$ 为前缀时，其值键值关系解析为“类似于”
``` javascript
{
	like2$id: 'foo'
}
// 代表
id LIKE '%foo'
```

> LIKE（非类似于）：以“字段名”作为键，但附加 _like$ 为前缀时，其值键值关系解析为“非类似于”
``` javascript
{
	_like$id: 'foo'
}
// 代表
id NOT LIKE '%foo%'
```

> LIKE（不以 Foo 开头）：以“字段名”作为键，但附加 _like1$ 为前缀时，其值键值关系解析为“类似于”
``` javascript
{
	_like1$id: 'foo'
}
// 代表
id NOT LIKE 'foo%'
```

> LIKE（不以 Foo 结尾类似于）：以“字段名”作为键，但附加 _like2$ 为前缀时，其值键值关系解析为“类似于”
``` javascript
{
	_like2$id: 'foo'
}
// 代表
id NOT LIKE '%foo'
```

``` sql

(id1 = 1) OR (
	(id2 = 1) AND
	(namezh = 'foo') AND
	(name = 'bar') AND
	(id <> 1) AND
	(id > 1) AND
	(id < 1) AND
	(id >= 1) AND
	(id <= 1) AND
	(date BETWEEN '2021-01-01' AND '2021-02-01') AND
	(date NOT BETWEEN '2021-01-01' AND '2021-02-01') AND
	(idx IN (1,2,3)) AND
	(idx NOT IN (1,2,3)) AND
	(id LIKE '%foo%') AND
	(id LIKE 'foo%') AND
	(id LIKE '%foo') AND
	(id NOT LIKE '%foo%') AND
	(id NOT LIKE 'foo%') AND
	(id NOT LIKE '%foo')
 )
```