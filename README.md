# github-handson

### GETリクエスト

* ターミナル結果
```
oyaminori@ooyasanenarunoMacBook-Air ~ % curl -i -u minori-oya:mytoken https://api.github.com/user
HTTP/2 200 
server: GitHub.com
date: Fri, 08 Sep 2023 10:04:21 GMT
content-type: application/json; charset=utf-8
...
{
  "login": "minori-oya",
...
 "created_at": "2023-06-29T09:54:08Z",
  "updated_at": "2023-09-06T22:20:48Z"
}
```
* POSTMAN結果
![GET](https://github.com/minori-oya/hello-world-blog06/assets/138114043/45547336-ca75-4605-9e48-dadbd4c6ff44)

### POSTリクエスト
* ターミナル結果
```
oyaminori@ooyasanenarunoMacBook-Air ~ % curl -i -H "Authorization: mytoken" \
    -d '{
        "name": "blog01",
        "auto_init": true,
        "private": true,
        "gitignore_template": "Nanoc"
      }' \
    https://api.github.com/user/repos
HTTP/2 201 
server: GitHub.com
date: Fri, 08 Sep 2023 10:19:37 GMT
...
{
 "name": "blog01",
...
 "private": true,
...
 "html_url": "https://github.com/minori-oya/blog01",
...
 "created_at": "2023-09-08T10:19:36Z",
  "updated_at": "2023-09-08T10:19:37Z",
...
 "visibility": "private",
...
```
* POSTMAN結果

![POST1](https://github.com/minori-oya/hello-world-blog06/assets/138114043/ec1227ca-7882-4b13-a6bd-2fcf65d51d10)

![POST2](https://github.com/minori-oya/hello-world-blog06/assets/138114043/b3f247b5-9c67-4432-8e29-8d033a3f284a)
d58-8e3f837388e0)


### PATCHリクエスト
1. リポジトリ名をblogからhell-world-blogに変更する
1. privateをpublicに変更
1. Aboutを"This is your blog repository"に変更
1. ホームページに"https://github.com" を設定

* ターミナル結果
```
curl -i -X PATCH \
  -H "Accept: application/vnd.github.v3+json" \
  -H "Authorization: mytoken" \
  https://api.github.com/repos/minori-oya/blog06 \
  -d '{
    "name":"hello-world-blog",
    "description":"This is your blog repository",
    "homepage":"https://github.com",
    "private":false
  }'
HTTP/2 200 
server: GitHub.com
date: Sun, 10 Sep 2023 02:33:28 GMT
...
{
...
 "name": "hello-world-blog",
...
 "private": false,
...
 "html_url": "https://github.com/minori-oya/hello-world-blog",
  "description": "This is your blog repository",
...
 "created_at": "2023-09-10T02:22:12Z",
  "updated_at": "2023-09-10T02:33:28Z",
...
 "homepage": "https://github.com",
...
 "visibility": "public",
...
```

* POSTMAN結果
![PATCH](https://github.com/minori-oya/hello-world-blog06/assets/138114043/f42a4654-0316-4f5c-8be7-d1971c612d3d)
