##提交补丁##

我们的项目是开源的，随时欢迎补丁！

您可以通过以下方式发送补丁：



Pull请求，就在git上。



联系我们https://rebrand.ly/teamwin-recovery-zulip-community



##保持作者身份##

保持作者身份是使用开源代码的一个非常重要的方面。如果您想提交补丁/修复程序

从其他任何地方（另一个ROM、项目等），您必须维护其所有者的所有权

你想要包括的工作。这样做将确保在应得的地方给予学分，以及

[开源原则](http://opensource.org/docs/osd)

得到支持。您对项目的贡献仍将得到认可，因为您将永远被列为提交者。



如果你手动挑选补丁/修复程序，那么在推送之前，你需要添加原作者

我们的[gerrit](https://gerrit.twrp.me). 这是一项非常容易执行的任务，通常在您提交

本地补丁/修复。这是在您键入“git commit-a”，键入commit消息并保存后完成的。你

然后将执行以下操作：



```bash

git commit--修改--作者“作者<email@address.com>"

```



因此，一旦你获得了作者的所有信息，它应该看起来像这样：



```bash

git提交-修改-作者“Spencer McGillicuddy<spencer.the.bestest@gmail.com>"

```



或者，添加作为原始“git commit”消息的一部分是首选，并按如下方式完成：



```bash

git commit--作者=“作者<email@address.com>“-m”[提交消息]

```



这节省了时间，当你的日常工作的一部分，防止臭名昭著的“ermahgerd我忘了添加作者-让

我修好了，因为我被发现了！“信息。




##入门指南##

要开始使用AOSP源代码构建TWRP，您需要熟悉

使用[Git和Repo](https://source.android.com/source/using-repo.html).



要使用AOSP树初始化本地存储库以构建TWRP，请使用以下命令：

    repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1

要初始化浅层克隆（这将节省更多空间），请使用以下命令：

    repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1

然后进行同步：

    repo sync

然后设置构建：

     cd <source-dir>; export ALLOW_MISSING_DEPENDENCIES=true; . build/envsetup.sh; lunch twrp_<device>-eng

构建目标取决于设备，应反映设备上库存回收的位置。发出适用于您的设备的构建命令：
- Recovery partition: `mka recoveryimage`
- Boot image ramdisk: `mka bootimage`
- Vendor_boot image ramdisk: `mka vendorbootimage`

###本分行特别提示

-设备树和依赖关系文件中的设备生成文件应使用“twrp”前缀。

-此分支目前不支持FDE解密。
