---
layout: post
category : Object-C
tagline: "Object-C Plist"
tags : [Object-C Plist]
---
{% include JB/setup %}

#Object-c中的plist读写

在IOS中，对于plist的操作，如果是项目中的plist文件，那么只能读，不能写，如果要写，那么我们只能在document中创建plist，直邮document中的文件，才可写。

假设，我们项目中有一个webservice.plist，我们首先将其copy到document中，然后在document中操作它。

	    id path = [[NSBundle mainBundle] pathForResource:@"WebServiceUrl" ofType:@"plist"];
    NSMutableDictionary *plist = [[NSMutableDictionary alloc] initWithContentsOfFile:path];
    
    if([userid isEqualToString:@"Test"])
    {
        //测试账号地址
        [plist setObject:TestAccountServiceAddress forKey:@"BaseDomain"];
    }
    else
    {
        //生产环境地址
        [plist setObject:ProductServiceAddress forKey:@"BaseDomain"];
    }
    //获取应用程序沙盒的Documents目录
    NSArray *paths=NSSearchPathForDirectoriesInDomains(NSDocumentDirectory,NSUserDomainMask,YES);
    NSString *docplistPath = [paths objectAtIndex:0];
    
    //得到完整的文件名
    NSString *filename=[docplistPath stringByAppendingPathComponent:@"DocWebService.plist"];
    //写入document
    [plist writeToFile:filename atomically:YES];

       