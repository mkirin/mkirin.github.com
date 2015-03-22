---
layout: post
title: Jesery 中文乱码
category : java
tagline: "Supporting tagline"
tags : [java,jesery,中文乱码 ]
---
{% include JB/setup %}
# Jesery 中文乱码
---
先看一下代码:

```
    @GET
    @Path("/hello/{user}")
    @Produces(MediaType.APPLICATION_JSON)
    public Response sayHello(
            @DefaultValue("0") @PathParam("user") String user,
            @Context HttpServletRequest request
    ) {
        JSONObject jsonObject = new JSONObject();
        try {
            jsonObject.put("你好",user);
        } catch (JSONException e) {
            e.printStackTrace();
        }
        Response response = Response.status(200).
                entity(jsonObject).header("Content-Type", "application/json; charset=utf-8").build();

        return response;

    }

```

<!--break-->
 需要注意是：`返回类型统一为Response  在返回的时候构造`

Response response = Response
                  .status(200)
                  .entity(jsonObject)
                  .header("Content-Type", "application/json; charset=utf-8")
                  .build();
```
其中:
+ entity() 传参为具体的返回类型
  * 比如Produces(MediaType.APPLICATION_JSON) 返回一个JSONObject即可
```

 

