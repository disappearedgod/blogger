---
安全—javascript-防止sql注入
---
SQL注入攻击的总体思路

*   寻找到SQL注入的位置
*   判断服务器类型和后台数据库类型
*   针对不通的服务器和数据库特点进行SQL注入攻击


#各种语言如何防止
1. javascript
	1. URL 地址防止注入：

	```javascript
	//过滤URL非法SQL字符
		var sUrl=location.search.toLowerCase();
		var sQuery=sUrl.substring(sUrl.indexOf("=")+1);
		re=/select|update|delete|truncate|join|union|exec|insert|drop|count|'|"|;|>|<|%/i;
		if(re.test(sQuery))
		{
			alert("请勿输入非法字符");	
			location.href=sUrl.replace(sQuery,"");
		}
	```

	2.输入文本框防注入 
	
	```javascript
		function AntiSqlValid(oField )
		{
			re= /select|update|delete|exec|count|'|"|=|;|>|<|%/i;
			if ( re.test(oField.value) )
			{
				//alert("请您不要在参数中输入特殊字符和SQL关键字！"); //注意中文乱码
				oField.value = ";
				oField.className="errInfo";
				oField.focus();
				return false;
			}
			...
		}
		//在需要防注入的输入文本框添加如下方法
		txtName.Attributes.Add("onblur", "AntiSqlValid(this)");//防止Sql脚本注入
	```
		 	  
2. node
	1. node-mysql  
3. Php
	1. Prepared Statements  
		*   采用预编译语句集，它内置了处理SQL注入的能力，只要使用它的setXXX方法传值即可。 