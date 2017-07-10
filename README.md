# 需求内容
	1. 为老师建立题库管理（出题＼导入＼统计）；
		为老师建立学生＼班级管理；
		为学生建立在线答题、自动反馈成绩的功能。
	
		
	2.	基本需求为：
			后台进行题库管理： 包括出题；导入题目和答案； 
					在excel中出题；（---奶老师可自主编制）
					题目按约定格式导入数据库，存入题库； 
					题库分页功能，对题目进行分页编制；
			
			后台进行用户管理： 包括对学生的管理（可扩充至家长信息）；
					登记学生信息；
					
			后台进行成绩管理： 包括对学生的选题管理、答题成绩管理（统计）；
					在线选题、答题、记录成绩；
					后台统计：对学生学习成绩进行分类汇总统计；
					
					
					

# 设计模型
		1.1  架构设计
		核心功能基于web网站。前端可基于APP、PC等，对H5页面进行访问。
		网站基于H5页面，后台连接RDB数据库，实现对题库的导入、用户及成绩的管理。
		出题管理，建议通过excel实现，以保持独立和灵活。
		
		1.2	系统基于开源软件，成本低
		操作系统：linux
		应用服务器：tomcat
		数据库： MySQL
		开发工具： java  (eclipse)
		
		1.3	数据库设计：
			用户表：
						userid						学生ID（自建）
						uername					学生名称
						password					密码
						gradeclass				班级
						tag							标签
						parent ( 1vsN)			家长们（多个，以json方式转换存储）
						contacts					 联系方式（多个，以json方式转换存储，建议手机号为主）
						

			导入题库表:
						titlename					题型名称
						pagename				题页名称（按导入日期时间编号）
						questionid				题目ID（到导入页的行序号）
						questiondesc			题目描述
						answer						标准答案
						uploaddate				导入日期
						tags (1vsN)				标签（多个，以json方式转换存储）
						
				题页表：
						examdate					题页编制日期
						titlename					题型名称
						pagename				题页名称（备注）
						pageno					分页编码（导入后分页获得。按tags汇总）
						questionid				题目ID
						questiondesc			题目描述
						answer						标准答案
						tags (1vsN)				标签（多个，以json方式转换存储）											
						
			成绩表：
					userid				学生ID
					titlename			题型名称
					pageno			分页编码
					resp_date			答题日期
					resp_time			答题时长
					resp_err			答案差错数
					resp_all				页面题目数
					
		1.4	web结构
				
				首页：（访客页面）
							宣传介绍
					
							登录页面：
									学生登录：
											学生信息查询：
													基本信息查询（默认页面）
													学习成绩查询
													成绩统计

													
									老师登录：
											题库管理：
													导入题库
													题库分页操作
													查询题库（默认页面）
													成绩统计
													
											学生信息查询：
													基本信息查询
													学习成绩查询
													成绩统计
													
											
									

				
				
				
					
