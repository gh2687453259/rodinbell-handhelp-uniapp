# rodinbell-handhelp-uniapp
rodinbell orca50 handhelp uniapp

1.0.5（2024-03-15） 完善罗丹贝尔手持机uhf的rfid 连接，扫码 ；


使用hbuilder 真机测试示例工程apk的时候需要使用自定义基座，使用前需要自行生成，方法自行搜索uniapp 官网。 plus：该插件最终没有在真实生产项目中使用，请自行测试是否合适再上线。

1. 引用插件
const uhfModule = uni.requireNativePlugin("rdbe-UHFPlugin-UHFModule");

2.初始化设备
var ret = uhfModule.createReader(nameid);

3.连接设备
var ret = uhfModule.callReaderUhf(nameid,JSON.stringify({ 'method': 'connectDevice', }));

4.盘点
var ret = uhfModule.callReaderUhf(nameid,JSON.stringify({ 'method': 'customInventory', }));

5.关闭连接
uhfModule.destroyReader(nameid);
