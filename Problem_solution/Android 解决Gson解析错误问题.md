
```
Gson gson = new Gson();
JsonReader reader = new JsonReader(new StringReader(result1));
reader.setLenient(true);
Userinfo userinfo1 = gson.fromJson(reader, Userinfo.class);
```