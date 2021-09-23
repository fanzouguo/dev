# tmind-dbProvider
The db provider base class for tFrameV9 of shanghai smpoo soft comoration.

## 前端标准 CRUD 请求参数

* ### 查询
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

* ### 新增
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

* ### 修改
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

* ### 删除
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
