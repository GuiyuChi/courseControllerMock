# courseControllerMock
根据controller标准组给出的json规范，伪造后端的json返回值，进而使前端的JS开发可以后台并行进行

Web 登录注册绑定

2.register--注册调用的接口    POST /register     
    http://rap2api.taobao.org/app/mock/933/POST/register
2.注册第二步，传输数据         PUT /me      
    http://rap2api.taobao.org/app/mock/933/PUT/me 

Web Teacher

1.Teacher--基本信息          GET /me    
    http://rap2api.taobao.org/app/mock/933/GET/me

2.Teacher--基本信息修改       POST /me  
    http://rap2api.taobao.org/app/mock/933/POST/me     (此处标准组原为patch，但经过询问改为post)

3.Teacher--教师主页（课程信息），显示课程信息    GET /course      
    http://rap2api.taobao.org/app/mock/933/GET/course （不知道如何生成多组不同的数据）

3.Teacher--教师主页（课程信息），保存修改的课程信息     PUT /course/{courseId}    
    http://rap2api.taobao.org/app/mock/933/PUT/course/1   (无法动态的传递数据，id写死)

4.Teacher--新建课程    POST /course    
    http://rap2api.taobao.org/app/mock/933/POST/course

5.课程内页--首页,通过id获取course    GET /course/{courseId}    
    http://rap2api.taobao.org/app/mock/933/GET/course/23

5.课程内页--首页，已创建的班级    GET /course/{courseId}/class    
    http://rap2api.taobao.org/app/mock/933/GET/course/23/class

5.课程内页--首页，已创建的讨论课    GET /course/{courseId}/seminars   
    http://rap2api.taobao.org/app/mock/933/GET/course/23/seminars

6.课程内页--创建班级，提交学生表格    POST /upload/classroster   （xlsx无法模拟）

6.课程内页--创建班级，提交信息    POST /course    
    http://rap2api.taobao.org/app/mock/933/POST/class   （按照赖神的规范为course，但发生了冲突）

7.课程内页--周三1-2节查看    GET /class/{classId}   
      （看不懂原来赖神的规范，然后现在的界面已经没有这张界面的图了？）

8.课程内页--周三1-2节修改   （问题同上，不知道一个参数的用处）

9.课程内页--创建讨论课   POST /course/{courseId}/seminar
    http://rap2api.taobao.org/app/mock/933/POST/course/23/seminar

11.课程内页--讨论课1,获得讨论课的基本信息    GET /seminar/{seminarId}
    http://rap2api.taobao.org/app/mock/933/GET/seminar/32

11.课程内页--讨论课1,获得讨论课的topic信息    GET /seminar/{seminarId}/topic    
    http://rap2api.taobao.org/app/mock/933/GET/seminar/32/topic

11.课程内页--讨论课1，删除讨论课    DELETE /seminar/{seminarId}

11.课程内页--讨论课1，删除讨论课    GET /seminar/{seminarId}

12.课程内页--修改讨论课信息    PUT /seminar/{seminarId}   
    http://rap2api.taobao.org/app/mock/933/PUT/seminar/32

14.课程内页--创建话题：    POST /seminar/{seminarId}/topic   
    http://rap2api.taobao.org/app/mock/933/POST/seminar/32/topic

17.话题A修改:查看该话题的JSON    GET /topic/{topicId}   
    http://rap2api.taobao.org/app/mock/933/GET/topic/257

17.话题A修改，提交     PUT /topic/{topicId}    
    http://rap2api.taobao.org/app/mock/933/PUT/topic/257

17.话题A修改，重置     GET topic/{topicId}

18.课程内页--评分，获取所有小组id   GET /seminar/{seminarId}/group
    http://rap2api.taobao.org/app/mock/933/GET/seminar/32/group

18.课程内页--评分，获得小组ID对应的小组详情的JSON    GET /group/{groupId}
    http://rap2api.taobao.org/app/mock/933/GET/group/28    （不知道如何生成多组不同的数据，只能生成两组相同的成员替代）

19.预览报告并打分  GET /group/{groupId}   

19.预览报告并打分，显示话题    GET /seminar/{seminarId}/topic   

19.预览报告并打分，确认打分    PUT /group/{groupId}/grade     
    http://rap2api.taobao.org/app/mock/933/PUT/group/28/grade


学生界面
1.基本信息，获取学生基本信息的JSON    GET /me   

2.基本信息修改，获取学生基本信息的JSON    GET /me   

2.基本信息修改，提交对学生基本信息的修改   PUT /me    

3.学生主页（课程信息），查询该学生关联的班级信息    GET /class     
    http://rap2api.taobao.org/app/mock/933/GET/class

4.选择课程 GET /class?courseName=*&teacherName=*  
     （带问号的语句，在mock服务器难以实现）

4.选择课程，学生选择课程    POST /class/{classId}/student    
    http://rap2api.taobao.org/app/mock/933/POST/class/34/student

6.课程内页-首页，已创建的班级   GET /course/{courseId}

6.课程内页-首页，已创建的讨论课    GET /course/{courseId}/seminar    
    http://rap2api.taobao.org/app/mock/933/GET/course/222/seminar

7.讨论课（随机分组），获取讨论课相关信息    GET /seminar/{seminarId}

7.讨论课（随机分组），学生所在的组的ID    GET /seminar/{seminarId}/group?include={studentId}    
   （带问号的语句，在mock服务器难以实现）

7.讨论课（随机分组），小组详情    GET /group/{groupId}?embedTopics=true    
    http://rap2api.taobao.org/app/mock/933/GET/group/28?embedTopics=true  （不知道如何生成多组不同的数据，只能生成两组相同的成员替代）

7.讨论课（随机分组），查看话题列表    GET /seminar/{seminarId}/topic 

8.讨论课（固定分组），获取讨论课相关信息     GET /seminar/{seminarId}

8.讨论课（固定分组），查看话题列表    GET /seminar/{seminarId}/group?include={studentId}
    （带问号的语句，在mock服务器难以实现）

8.讨论课（固定分组），选择话题    POST /group/{groupId}/topic    
    http://rap2api.taobao.org/app/mock/933/POST/group/28/topic
8.讨论课（固定分组），上传报告PDF文件    POST /upload/report    
    (无法识别pdf文件)

8.讨论课（固定分组），将报告PDF文件位置写入小组表    PUT /group/{groupId}   
    http://rap2api.taobao.org/app/mock/933/PUT/group/28

9.固定分组 ，查询现有学生信息    GET /class/{classId}/classgroup    
    http://rap2api.taobao.org/app/mock/933/GET/class/34/classgroup
10.固定分组修改页，展现现有学生信息     GET /class/{classId}/classgroup 

10.固定分组修改页，查询学生    GET /class/{classId}/student?nameBeginWith=张    
    （RAPmock服务器无法识别包含问号的语句）        

12.查看分数，得到该学生的小组分数    （感觉标准组目前的实现存在问题，已经提出）



说明：此文档是为实现前后端分离而进行的努力。采用阿里RAP服务器，根据controller标准组给出的json规范，伪造后端的json返回值，进而使前端的JS开发可以后台并行进行。
适用人群：了解前后端传值方式的前端JS脚本编写人员。
免责声明：此文档为本人自用工具的共享，依据标准组文件编写，但是编写时间仓促，故不能保证完全正确，一切以标准组规范为准。

使用方法：该文档分三列，第一列为在controller标准组给出文档中对应位置。第二列为标准组给出的URL，第三列为获取mock虚拟JSON的url
在测试时将第三列替换ajax中的url，即可获得测试json，待controller完成，将测试url换成标准组给出的标准url，即可与controller完成对接
时间仓促，排版匆忙，建议使用vscode打开，并且改用CTRL+F方式查找食用
本组选择web端，对小程序逻辑不熟悉，故只完成web端工作
本文将会发布于github，并根据修改意见进行更新，欢迎通过QQ，微信和Issues发送修改意见
