---
layout: post
category : DotNet
tagline: "Hello world"
tags : [Hello World]
---
{% include JB/setup %}

#Block in Objec-C

首先，在头文件中定义一个自定义类型:

	typedef void (^SuccessBlock) (NSString *json);
	
void表示没有返回值,SuccessBlick是Block的方法名，最后的是方法签名

然后定义一个属性:

	@property (strong,nonatomic) SuccessBlock success;

这样，一个block就声明好了。在实现的文件中，可以对其进行赋值和调用。

下面看看在头文件中如何实现。

假设我们有这么一个方法

	-(void) Invoke:  withJSON:(NSString *)content 
	successblock:(void (^)(NSString *json))successblock
	{
	     self.success=successblock;
	}
    -(void)FinishedInvoke
    {
    	self.success(@"{code:'1',returnvalue:'2'}");
    }

在其它地方，可以这样调用Invoke

	[Helper Invoke:@"{data:'aa'}" successblock:^(NSString 		*json){
		NSLog(json);
	}];
