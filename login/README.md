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
	start:	date1
	end:	date2
	</pre>
4. 实训组名册由

###实训营名册
范例：
<pre>
	workshop: workshop_id
	team:
	  - info: http://teamserver1/teaminfo.yaml
	  - info: http://teamserver2/teaminfo.yaml
	  - info: http://teamserver3/teaminfo.yaml
	  - ...
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
3. member：
	1. id： 成员ID。
	2. pubkey： 成员的公钥，各人在自己机器上创建后提交给实训营。