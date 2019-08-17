# vue-questionnaire

> 简易问卷系统,目前功能正在逐步完善中...

> 由于本系统用于校内学生，所以在提交问卷时需要先查看用户的有效性（参与问卷调查的人员是可控的），如不需要此功能，可以自行修改代码。

## 功能
1. 创建问卷、删除问卷、预览问卷、编辑问卷截止时间
2. 问卷结果统计，样本数据查看，已填写问卷用户查看
3. 使用 Excel 批量导入用户、批量删除用户，单个添加、修改、搜索、删除用户
4. 问卷调查页面适配移动端
5. 问卷单题目交叉分析

## TODO
1. 编辑问卷（未发布状态）
2. 查看问题选项所选人员信息（姓名、班级）
3. 修改用户已填写的选项

## 前端部署说明

前端文件存放于 `/front-end/ ` 文件夹下

``` bash
# 安装依赖
npm install

# 服务热重载地址：localhost:8080
npm run dev

# 线上部署编译
npm run build

```

## 前台配置
### proxyTable

如果遇到访问接口出现

> Error occured while trying to proxy to: localhost:8080/api/admin/test`

可以参照下面方法解决：

如将 `/api` 文件夹放在了 PHP 环境中的 `vue-questionnaire` 文件夹中，且访问地址为：`http://localhost:8888/vue-questionnaire/api` ，那么可以根据我的配置来使用了。

同时也可以根据本地PHP环境的访问地址来修改 `/config/index.js` 中 `proxyTabel` 相关配置。


### API接口请求地址

修改 `/src/config/index.js` 中的 `baseURL`

### adny的配置
我这里是LAMPP apache做服务器，自带php处理器 挂载80或者443端口上
然后在 `front-end/config/index.js` 中改成如下
```js
  dev: {
    env: require('./dev.env'),
    port: 9090,
    autoOpenBrowser: false,
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    // 解决跨域问题
    proxyTable: {
      '/api': {
        target: 'http://localhost:80/vue-questionnaire/',   //重要的是这个地方，这里是由php处理器处理的api，lampp上apache的端口是80，所以这里调成80，其他请按照相关配置自行修改
        changeOrigin: true,
        pathRewrite: {
          '^/api': '/api'
        }
      }
    },
```
然后就可以使用了

## 后台配置
数据库文件： `api/database.sql`，使用前请先导入。

CI框架数据库连接配置信息请先设置。

### andy的配置
在本机mysql环境下导入sql后
在 `api/application/config/database.php`文件中修改相应配置即可


## 微信公众号相关
### TODO
1. 接入公众号平台接口登陆
2. 使用公众号账号作为唯一用户
3. 可关注公众号二维码

## 打赏
如果我的付出能够帮助到你，我也乐于接受你的帮助，小小的赞赏是我们持续进步的动力。


昵称 | 金额
---|---
[Little Mo](https://github.com/one-mo) | ￥50.00
[mike](https://github.com/zhezhe168) | ￥1600.00
[stepven8](https://github.com/stepven8) | ￥50.00

![支付宝支付](https://blog.52admin.net/wp-content/uploads/2017/09/alipay.png)
![微信支付](https://blog.52admin.net/wp-content/uploads/2017/09/wechat.png)
