

```
Gson gson = new Gson();
JsonReader reader = new JsonReader(new StringReader(result1));
reader.setLenient(true);
Userinfo userinfo1 = gson.fromJson(reader, Userinfo.class);

```

[此处输入链接的描述][1]


  [1]: https://github.com/square/retrofit/issues/1465