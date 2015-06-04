##登录控制器
任务设计

###任务简介
本任务模拟一个真实的登录控制器，它具有以下特性：

1. 哈希：只保存SHA512哈希值，不保存密码明文。哈希运算在服务端完成。
2. 加盐：哈希函数的输入不是密码，而是加盐的密码。
3. 随机性：盐值使用基于加密的伪随机数生成器（Cryptographically Secure Pseudo-Random Number Generator：CSPRNG）。
4. 使用http，不需要https。
5. 不需要OAuth等验证。


###作品接口
1. user register
	1. method: HTTP POST
	2. path: http://teamserver/memberid/login/reg
	3. body: yaml string
		<pre>
			username: samplename
			password: abc123！@#
		</pre>
	4. return：
		* 201 CREATED
		* 400 INVALID REQUEST
		* [其它可选](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) 
	
2. user login
	1. method: HTTP POST
	2. path: http://teamserver/memberid/login
	3. body: yaml string
		<pre>
			username: samplename
			password: abc123！@#
		</pre>
	4. return：
		* 202 Accepted
		* 401 Unauthorized
		* [其它可选](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) 

###实训组名册
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

###实训营名册
<pre>
	workshop: workshop_id
	team:
	  - info: http://teamserver1/teaminfo.yaml
	  - info: http://teamserver2/teaminfo.yaml
	  - info: http://teamserver3/teaminfo.yaml
	  - ...
</pre>