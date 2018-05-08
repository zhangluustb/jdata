# jdata 用户购买时间预测
[如期而至-用户购买时间预测](https://jdata.jd.com/html/detail.html?id=2)
> 利用 **用户历史行为数据**，预测*热销品类*的 **用户购买时间**。

用户————商品————是否复购？

0. pre分析决定 target
- 分析label是否主要受历史label影响
- 分析label与哪些其他特征联系最紧密

1. basic features
- category features: sex,user_lv_cd cate o_area
- 没有测试集当时的流数据，缺少类似每天‘促销信息’，‘每天的节假日信息’

2. 统计特征 [time_windows dim target method]
- time windows
	nearest days: [1,3,5,7,14,30,60,140]
	equal time windows: [1] * 16, [7] * 20...

- dim：store x item, item, store x class

- target: promotion, unit_sales, zeros

- method
	mean, median, max, min, std
	days since last appearance
	difference of mean value between adjacent time windows(only for equal time windows)

3. useless features
	holidays
	other keys such as: cluster x item, store x family

