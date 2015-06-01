##Information Technology Workshop

###概述
1. 本模型由旧版本ITW模型与[定单式实训](https://github.com/hyg/com.origin/blob/master/Order.Training/Order.Training.md)合并产生，IT高教版也结合了[MDW模型](http://git.oschina.net/hyg/MDW/blob/master/README.md)的部分内容。
2. ITW是学门科技JPU立项的产品，是[联合提货权](https://github.com/hyg/com.origin/blob/master/Joint.Token/Joint.Token.md)的**普通使用者**。

###角色清单
* 产品经理
* site admin
* server admin
* 任务设计者（task designer）
* 课程提供者
* 学习者

###资产清单
* 任务备忘录
	* 任务简介
	* 接口说明
	* 测试器信息
	* 价格
	* 任务设计者信息及签名
* 课程备忘录
	* 课程简介
	* 能力结构
		* 任务一
		* 任务二
		* ...
	* 面授模式
		* 课时安排
		* 首课信息
		* 课程价格 
	* 在线模式
		* 课时安排
		* 首课信息
	 	* 课程价格
	* 课程提供者信息及签名
* 线下实训备忘录
	* 课程介绍
	* 
	* 预售数额和价格 
* 线上实训备忘录
	* 

* 

###接口清单

* 任务
	* 创建
	* 
* 课程
	* 创建
	* 预售
* 线下实训
	* 创建
* 线上实训
	* 创建
	* 
 
* 

###协作过程
* 任务
	* 创建:
		1. 任务设计者向产品经理提交《任务备忘录》。
		2. 产品经理验证数字签名后公布。
	* 

* 课程
	* 创建：
		1. 课程提供者向产品经理提交《课程备忘录》。
		2. 产品经理验证数字签名后公布。
* 线下实训
	* 创建
		1. site admin根据《课程备忘录》开设线下实训课程。
		2. 
* 线上实训
	* 创建
		1. server admin可以
	* 
	* 预售：
		1. 学习者、site admin（针对面授课程）、server admin（针对在线课程）都可以预购课程。
		2. 
	* 

###分配规则