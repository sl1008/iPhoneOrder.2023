## iPhoneOrder.2023

<b>2023版 iPhone 自动抢购插件</b>

苹果官网本身并未限制 iPhone 下单，但选择配送可能交付时间过长。该插件用于自动捡漏可门店自提的订单。


<b>********** 该插件仅用于学习和交流 **********</b>

<b>请注意: 本项目采用 [Bun](https://github.com/oven-sh/bun) 进行打包和启动, 与npm略有不同。</b>

------

## 说明

鉴于目前抢购热度已经消退，重新开放 Readme，但为了避免不必要的麻烦，该项目不出包。可以自行查看[如何自行打包](#fork_change)部分进行打包生成插件。

You can fork this repository, modify codes or fix bugs by yourself, and build a release.

Thanks.

------


[Q & A](#q_a)
<br/>

[安装和使用](#install)
<br />

[更新日志以及遗留问题](#update_info)
<br/>

[如何自行打包](#fork_change)
<br/>

------

<a id="q_a"></a>

# Q & A

- **Q:**  这是一个什么东西？<br />
  **A:**  这是一个 Chrome/Edge 浏览器插件，用于检测苹果门店是否有剩余的新款 iPhone，并且自动捡漏下单。

- **Q:**  我该如何使用？<br />
  **A:**  请看文档中的安装和使用。

- **Q:**  我看到配置项中需要输入密码，这安全吗？<br />
  **A:**  密码仅用于下单时登陆苹果账号，捡漏的订单可以直接绑定在你的 Apple ID上。

- **Q:**  我不相信你，我可以不填密码吗？<br />
  **A:**  是的，你完全可以不填密码。在不填密码的情况下也可以正常使用，插件会以访客模式下单。

- **Q:**  你的插件安全吗？<br />
  **A:**  插件所有代码开源可查，如果你是一名程序员，你甚至可以逐行 review 我的代码。如果你是知道如何使用 DevTools，也可以打开它来检查网络请求。当然你的疑虑是正常的，请不要过分相信互联网上的任何人。如果你的安装包并非来自这里，请更加谨慎对待。

- **Q:**  我在我的Chrome中安装插件报错，为什么？<br />
  **A:**  本插件使用 manifest v3.0, 请安装最新版 Chrome 或者 Edge，最少也要 Chrome 88 以上的版本。尽量更新到最新版。v0.9之后的版本增加了 tts 权限，最少需要 Chrome 101 以上的版本。

- **Q:**  为什么我看页面没有任何反应，它真的在抢购吗？<br />
  **A:**  是的，代码是在后台静默调用接口，可以按 F12，打开 DevTools，查看控制台里面的 log 信息，并且也可以查看网络请求调用。

- **Q:**  显示抢到了，但是无法支付怎么办？点击支付按钮没有任何反应。<br />
  **A:**  很遗憾，这种情况大概率是没有抢到。请检查你预填的手机和邮箱是否有接收到订单提醒。如果没有收到任何消息，并且购物车中的 iPhone 还存在，那么就是没有抢到。

- **Q:**  为什么呢？不是显示成功就是抢到了吗？<br />
  **A:**  由于下单接口返回的数据并不准确，插件仅判断下单接口是否成功返回作为成功依据。因此，最后的页面实际只是一个消息提示，并不真正表示成功。

- **Q:**  我下单成功了，但是订单中的城市不是我所在的城市？<br />
  **A:**  没关系，由于苹果网站定位的问题，可能会导致部分场景下调用接口的城市错误。只要你所选择的取货店铺正确即可。

- **Q:**  我可以同时抢购多部 iPhone 吗？<br />
  **A:**  由于浏览器的插件在一个配置中是共享的，所以一个浏览器配置只能抢购一部。

- **Q:**  那我真的想多部 iPhone 同时捡漏可以吗？<br />
  **A:**  也是可以的，请开多个 Chrome 个人配置，每个配置单独安装插件，他们之间互不影响。

- **Q:**  这样会被封 IP 吗？<br />
  **A:**  如果你一次开多个配置浏览器同时抢购，是可能被封 IP 的，但插件有做处理，当接口无法访问时，会增加步频等待时间，直到接口再次可以被访问。

- **Q:**  这样会被封苹果账号吗？<br />
  **A:**  我无法明确回答这个问题。但如果你不放心，可以填写不常用的邮箱地址，并且不要填写密码，这样就以访客模式下单，不会对你的账号造成任何影响。

- **Q:**  我只要配置好就可以了吗？<br />
  **A:**  差不多，但需要注意的是，请保持电脑不要休眠。插件其实只是替代你来职守，电脑需要保持常开状态。

- **Q:**  如果半夜抢到了，但我睡着了怎么办？<br />
  **A:**  插件 v0.9 以后的新增语音提醒功能，请在配置中自行设置需要提醒的话术以及次数。能不能叫醒看是否睡的沉。

- **Q:**  抢购成功率高吗？<br />
  **A:**  插件的功能只是捡漏，如果其他人有更快的秒杀工具，此插件应该没什么优势。捡不到是正常，请放平心态。
<br />

------

<a id="install"></a>

### 安装和使用
1. ~点击下载安装 [Release](https://github.com/loo-y/iPhoneOrder.2023/releases/)~ 请自行参照[如何自行打包](#fork_change)生成插件

2. 解压缩到本地任意目录

3. 打开Chrome 或者 Edge 浏览器

4. 找到管理扩展程序
   <br/><img src='./public/assets/images/SCR-20230916-nbkz.png' width="800px" />

5. 开启开发者模式， 点击 "加载已解压缩的程序" 
   <br/><img src='./public/assets/images/SCR-20230916-nbyv.png' width="800px" />

6. 选中刚才解压缩的 iPhoneOrder 文件夹
   <br/><img src='./public/assets/images/SCR-20230916-ncte.png' width="600px" />

7. 安装成功之后可以在扩展程序中看到已应用
   <br/><img src='./public/assets/images/SCR-20230916-ndgw.png' width="600px" />

8. 点击左上角扩展程序标志，找到 iPhoneOrder 并固定
   <br/><img src='./public/assets/images/SCR-20230916-ndks.png' width="350px" />

9. iPhoneOrder将被固定在右上角，点击打开，选择配置
   <br/><img src='./public/assets/images/SCR-20230916-neaa.png' width="350px" />

10. 填写必要的配置信息
   <br/><img src='./public/assets/images/SCR-20230916-neeq.jpeg' width="800px" />

11. 打开 苹果官网，将想要的 iPhone 预先放入购物车，点击开启，并确认。刷新页面即可。
   <br/><img src='./public/assets/images/SCR-20230916-nfkt.png' width="800px" />

<br/>

补充：
1. 新增浏览器系统通知，请点击插件图标，点击 通知测试 按钮。
<br/><img src='./public/assets/images/SCR-20230919-ulfn.png' width="350px" />

2. 等待浏览器网址栏左侧弹出询问窗口，点击同意。
<br/><img src='./public/assets/images/SCR-20230919-uocr.png' width="350px" />

3. 允许通过之后，窗口右侧就会弹出系统通知。(Windows 可能在桌面右下角)
<br/><img src='./public/assets/images/SCR-20230919-ulzd.png' width="350px" />

4. 之后如果抢到订单，就会弹出通知，避免错过消息。

<br />

------

<a id="update_info"></a>

### 更新日志以及遗留问题
#### 2023.10.07
bun 1.02 有bug导致 node:fs 的异步操作并没有生效，但不影响实际打包。

#### 2023.09.19
v0.10, 新增浏览器系统通知功能。

#### 2023.09.18
新增 v0.9 版本，该版本新加入语音提醒功能，此功能需要获取 tts 权限，并且限制 Chrome 101 以上版本。

#### 2023.09.17
遗留问题

1. ~~苹果调整了取货店铺信息的接口，插件需要调整；~~ (已修复)
2. ~~注入 history.pushState 的方式目前未生效，导致页面跳转之后没有继续执行。~~(已修复)
3. 由于插件中的 省份/城市/地区 数据并非来自苹果的店铺页面，可能产生配置中的区域和页面对不上，导致始终无法获取到最新的取货店铺。也可自己修改 shared/location 目录中的信息，重新编译打包使用。

<br />

更新内容

>v0.5 版本已走通 iPhone 15 新款的流程。
>
>新款和老款在取货上的区别是，新款会增加到店取货时间，以及在选择时间时会校验签名，此流程已走通。
>
>目前 v0.5 在选择自提店铺页面时，后台会不断请求配置中填写的区域店铺，页面上展示的地址可能与配置中的地址不同，这个不影响最后下单时的取货店铺。
>
>当后台匹配到与配置中填写城市相符的店铺有货时，会自动下单，取货店铺页会一步到达付款页。
>
>如果自己手快点击下一步，也会自动填写信息下单。
<br/>

------

<a id="fork_change"></a>

### 如何自行打包
如果你是一名程序员，你想自己二次开发：

本项目前端框架使用 Nextjs + tailwind CSS， 打包和安装通过 [Bun](https://github.com/oven-sh/bun)，可以先去 Bun 网站查看如何安装。

Bun 和 node + npm 的差异并不是很大，如果你之前是一名程序员，应该不难上手。

如果实在不想使用 Bun，也可以通过 npm 安装。但 bunBuild.ts 这部分的代码需要自行调整。 另外 package.json 中的 script 也包含了部分 Bun 命令，可以使用 npm 替换。

如果你已安装好 Bun，和 npm 一样，先```bun install```，然后开始修改代码。在修改完代码之后，只需执行 ```bun build:extension``` 即可。 此命令会自行打包文件至 extension 文件夹， 并且生成 zip 包。

以上基于 Mac (Apple silicon) 环境， 如果是 windows，部分命令可能需要再次调整。

<br/>

------
