##Information Technology Workshop
IT类高教版

###概述
1. 本模型由旧版本ITW模型与[定单式实训](https://github.com/hyg/com.origin/blob/master/Order.Training/Order.Training.md)合并产生，也结合了[MDW模型](http://git.oschina.net/hyg/MDW/blob/master/README.md)的部分内容。
2. ITW是学门科技JPU立项的产品，是[联合提货权](https://github.com/hyg/com.origin/blob/master/Joint.Token/Joint.Token.md)的**普通使用者**。

###角色清单
* 产品经理：product manager
* 实训主任：workshop admin
* 学员：learner
	* 组长：team leader
	* 组员：team member
* 任务设计者：task designer
* 课程提供者：course provider
	* 讲师lecturer
* 助教：teaching assistant（可能来自课程设计者或实训主任）

###资产清单
1. 记账单位
	1. 人民币
	2. 联合提货权
2. 信息资产
	* 实训简章
		* 课时安排
		* 作品提交期限
		* 淘汰规则
		* 报名颁发
		* 费用说明
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
	* 服务器配置

###接口清单
* 创建workshop
* 第一节课
* 后续课程 
* 选课（可选）

###协作过程
* 创建workshop
	1. 任务设计者发布《任务备忘录》。
	2. 课程提供者发布《课程备忘录》。
	3. 实训主任发布《实训简章》。
	4. 学员报名缴费，加入实训营。
* 第一节课
	1. 助教讲解实训组的功能和角色权责，演示小组服务器的基本创建步骤。
	2. 学员根据意愿选择创建或加入实训组，如果所有学员均不创建实训组则由助教创建：
		1. 组长建立服务器，发布《服务器配置》；
		2. 组员选择至少一个实训组。
	3. 组长会议完成以下工作：
		1. 将所有独立学员分配到实训组。
		2. 编写《实训营名册》并提交给实训主任。
* 后续课程 
	1. 实训主任按照《实训简章》中的课时安排组织面授。
	2. 课堂上，讲师负责讲解技术原理和操作步骤，助教负责辅导组员。
	3. 课堂外，组长负责辅导组员，确保组员的作品托放在服务器上。
	4. 每个任务对应课程完成后，任务设计者按照《实训简章》中的安排访问各小组服务器，检验学员的作品，发布分数。
	5. 任务设计者发布分数后，讲师按照《实训简章》中规定的淘汰规则宣布解散的实训组。
	6. 被解散的实训组组长、成员各自选择加入其它实训组。
	7.  组长会议完成以下工作：
		1. 将所有独立学员分配到实训组。
		2. 编写《实训营名册》并提交给实训主任。
* 选课（可选）
	1. 实训主任定期汇总《任务备忘录》、《课程备忘录》，召集实训组组长审议。
	2. 以各组成员人数作为权重，组长对后续课程进行表决。
	3. 实训主任按照表决结果预购课程，更新《实训简章》。
	4. 学员续签教学协议。

###分配过程
1. 实训营的学费包括：
	* 任务：JT，任务设计者。
	* 课程：JT，课程提供者。
	* 讲师：JT，讲师。
	* 助教：JT，助教。
	* 实训组：人民币，实训组长。
	* 实训营：JT，实训主任。
	* 项目组：JT，产品专户。
	* 杂费：人民币，实训主任。
2. 学员缴纳人民币的，由产品经理统一指定兑换处换取JT。ITW内统一流通JT。
3. 实训组和杂费，由产品经理统一指定兑换处换取人民币。


###实训组名册
范例：
<pre>
	leader: leader_id
	server: http://teamserver
	member:
	  - id: member1_id
	    sig: member1_sig
	  - id: member2_id
	    sig: member2_sig
	  - ...
</pre>
1. leader_id: 实训组组长的ID
2. server: 实训组服务器的入口网址
3. member
	1. id： 成员的ID
	2. sig： 成员使用密钥对以下数据的签名：
	<pre>
	leader: leader_id
	task:	task_id
	</pre>
4. 实训组名册由实训组长维护。

###实训营名册
范例：
<pre>
	workshop: workshop_id
	team:
	  - info: http://teamserver1/teaminfo.yaml
	  - info: http://teamserver2/teaminfo.yaml
	  - info: http://teamserver3/teaminfo.yaml
	  - ...
	alloc:
	  - id: member1_id
	    leader: leader_id
		task: task_id
	  - id: member2_id
	    ...
	member:
		- id: member1_id
		  pubkey: |- 
		  -----BEGIN PGP PUBLIC KEY BLOCK-----
		  Version: OpenPGP.js v0.9.0
		  Comment: http://openpgpjs.org
		
		  xsBNBFSlVgcBCACQURxJMfdrPbAFa5ZGOs4j43tRmc7KQoM6lKveobO+v+Jg
		  IIYqXtDadXAM1h34CQgwj4o7VFKf+M1SmGbO57cx+M3U1+SgKmW9w8gRwgNE
		  q+m3JPo+HIiOI/X8Gsa9vrbAbs19UvXk4H+CdC02bxwruLPan87fI17wGLEB
		  62mcLG9eNPg4XrmZDDISPvicR88AFmkZMPh9WoVm99jzKl3EWCfPXqdNiLWK
		  kzXZO2jPLXLb2iJRacq2i+QXt5UWB5BEaAHLLVLTu5PNykHumN0xxIoidrxV
		  G+ug8Z269ZmcYdRv2fgY/TYP+/h43RkSI+iqiXeKSL8+WGDqSpee9sPnABEB
		  AAHNMOa1i+ivlei0puWPtyAoaHlnL2pzLnNhbXBsZSkgPHRlc3RAanNzYW1w
		  bGUub3JnPsLAcgQQAQgAJgUCVKVWDwYLCQgHAwIJEE5QeumSjbLwBBUIAgoD
		  FgIBAhsDAh4BAADijgf/e24fcRYoEZlIrej5ZblOszkKV7Y2900NerwrLPFK
		  kfQVHOBSAi9Nls5rOlZ4jDi7rd8/V+NUDDqE966jMha6TpCnHd+j6I4tiJiq
		  I8n51FoctVcpJcadygcoZE18pGF+dl62o7iLJVqsQv6ZnbLTQJngPDjAQGG8
		  KKhJjpY2RYNnR8vBCb4+lH8lhBnXviUUyyFRBjbBdhiPVebvv/LGd60diEmJ
		  +xKC89+Z0bGdElPpVW2WdOkTXL47UoNfZpHzpxhytOmjAykxGFtaqtUmHzvN
		  KogM5YDXuO7ZcWjiiTbKSnLcYyWLBp8VGq+MdDQmIEV7YpE3/mWPHat0wZar
		  X87ATQRUpVYMAQgAogdxHIK2i4MMeV2DASacwP037GCqyLHRcmo1ud5IYkHd
		  WXs1xigEklj2+3AaWjYgHzhN/f5BE2aDFttSonJhQ+ltZrEArungIWppSfN+
		  v6SyzmUsYK8EooF1M/EckvyF3ugub+SGst4MXyGfYhx901oRvKhY61pFWgZP
		  3gs/P1nHbDpUYNDKENflVBV0ha2DSlLxFQdfSh4hh4Jm1icmw85V5gTwppQd
		  CQ//qGZ757Tq4AtZS9givMYnSkXFsSlufKZ8LTVa/RFZ+gGKbcJHMR8XLoOc
		  8n8Vge92GHm63W5mP33A99e+NgyegInLmoi3lIXGO8yORIdwci17Eaqa9QAR
		  AQABwsBfBBgBCAATBQJUpVYQCRBOUHrpko2y8AIbDAAAmiAIAIHhfGiJ9e9L
		  n8z9tD/BFzqk5vll36hCXkLdg2HzftJsxPdW0eT27iDLagJcsrbVpRAag49/
		  47GH9BeHdtqsDNsh7UzQAlfp4t7+Fi00+9GuazHtTnI1bN9zgpGLCCNP6JUR
		  J9Z00c+GhQayTkPwTCf9zCidtbbNJc7GRlfgOMaoNqGoasyZrltqoB6hCM16
		  l0jkh59MIqQ+4FbLQOqr/7SGi6H1wzFa/Q4Q9R2VDg5zlEg163pbsf+ope52
		  3rPxBia7vxpFfXQXGbtR6vZDjI8uqsEMEyflqiuHJxmjtitnYLRqxQRr9fZq
		  WMc+ZlpNrplXO9WkeuhEICGQdZSy/ok=
		  =+yKz
		  -----END PGP PUBLIC KEY BLOCK-----
		- id: member2_id
		  ...
</pre>
1. workshop： 实训营的ID
2. team：
	1. info： 当前有效的实训组名册，是一个公网可访问的yaml文件。
3. alloc: 未选择实训组的学员，由组长联席会议直接分配。
	1. id: 学员的ID
	2. leader：被分配到的实训组组长ID
	3. task: 任务的ID
4. member：
	1. id： 成员ID。
	2. pubkey： 成员的公钥，各人在自己机器上创建后提交给实训营。
5. 实训营名册由组长联席会议维护。