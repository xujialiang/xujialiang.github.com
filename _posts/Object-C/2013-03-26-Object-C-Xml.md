---
layout: post
category : Object-C
tagline: "Object-C Xml"
tags : [Object-C Xml]
---
{% include JB/setup %}

#Object中的xml解析

在object-c中又许多解析xml的开源类库，以及苹果自带的类库。看着哪个顺眼就用哪个吧。我这里用了[kissxml](https://github.com/robbiehanson/KissXML)

用法也非常的简单，首页初始化document
	
	DDXMLDocument *xml=[[DDXMLDocument alloc] initWithXMLString:xmlstring options:0 error:nil];

然后就可以通过解析节点进行取值了。具体用法，看官方的文档了。这里只是抛砖引玉。
        
        DDXMLNode *resultbody = [xml childAtIndex:0];
        //soap消息中错误代码
        DDXMLNode *resultcode=[resultbody childAtIndex:0];
        //返回的xml
        NSString *returnxml=[[[resultbody childAtIndex:1] childAtIndex:0] XMLString];
        //错误信息
        NSString *errorxml=[[[resultbody childAtIndex:2] childAtIndex:0] XMLString];
       