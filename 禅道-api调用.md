GET/POST  /zentao/bug-create-[productID]-[branch]-[extras].json 
/zentao/bug-create-1.json

bug-create-1-0-moduleID=0.json


http://10.7.91.104:8090/zentao/bug-create-1-0-moduleID=0.html

http://10.7.91.104:8090/zentao/bug-create-1-0-moduleID=0.json?product=1&title=test&openedBuild=trunk


{
    "status": "success",
    "data": "{\"title\":\"\",\"sessionName\":\"zentaosid\",\"sessionID\":\"ciq5tbld3sl47dk6ep4a9uvt87\",\"rand\":3410,\"pager\":null}",
    "md5": "c0ab99985948aff1bc4ae4dbaf1a12a9"
}

#获取session
zentao/api-getsessionid.json

#使用拿到的sessinid登录

zentao/user-login.json?zentaosid=ciq5tbld3sl47dk6ep4a9uvt87
account
password

#创建一个任务

/zentao/task-create-[projectID]-[storyID]-[moduleID]-[taskID]-[todoID].json



/zentao/task-create-7--0.json?zentaosid=ciq5tbld3sl47dk6ep4a9uvt87&t=json

type design

name test

assignedTo zhangle



zentao/user-login.json?zentaosid=ciq5tbld3sl47dk6ep4a9uvt87

task-create-1-1-3.json?zentaosid=ciq5tbld3sl47dk6ep4a9uvt87&t=json



insert into zt_task 
select 

100,parent,project,module,story,storyVersion,fromBug,'123',type,pri,estimate,consumed,`left`,deadline,status,color,mailto,`desc`,openedBy,openedDate,assignedTo,assignedDate,estStarted,realStarted,finishedBy,finishedDate,finishedList,canceledBy,canceledDate,closedBy,closedDate,closedReason,lastEditedBy,lastEditedDate,deleted
from zt_task where project=7;



perl get_tablename.pl CIRC3_MDATA|while read table_code

do

jdva -jar /dta/script/td_export/bin/td_exp_gp.jar ${table_code}_${last_month} CIRC3_MDATA backup_data_circ3 /dta/script/td_export ${table_code}
done

perl get_tablename.pl CIRC3_MDATA|while read table_code
do
java -jar /dta/script/td_export/bin/td_exp_gp_all.jar ${table_code}_${last_month} CIRC3_MDATA backup_data_circ3 /dta/script/td_export ${table_code}

done



{
    "status": "success",
    "data": "{\"title\":\"\数\据\同\步\平\台::\提Bug\",\"products\":{\"2\":\"\保\单\登\记\",\"1\":\"\数\据\同\步\平\台\",\"5\":\"\管\理\提\升\",\"4\":\"\寿\险\战\报\",\"3\":\"\数\字\化\中\台\"},\"users\":{\"\":\"\",\"baigenhai\":\"B:\白\艮\海\",\"chendong\":\"C:\陈\栋\",\"duyangguang\":\"D:\杜\阳\光\",\"gaojie\":\"G:\高\杰\",\"huangqiaoling\":\"H:\黄\巧\玲\",\"liuliting\":\"L:\刘\莉\婷\",\"liutianlun\":\"L:\刘\天\伦\",\"liuxiaoyu\":\"L:\刘\晓\宇\",\"loujie\":\"L:\娄\洁\",\"luyi\":\"L:\陆\怡\",\"luyuan\":\"L:\陆\远\",\"sunguoliang\":\"S:\孙\国\亮\",\"wangmin\":\"W:\王\旻\",\"wudi\":\"W:\吴\迪\",\"zhangjingwei\":\"Z:\张\景\伟\",\"zhanglei\":\"Z:\张\磊\",\"zhangyunjia\":\"Z:\张\运\佳\",\"admin\":\"A:admin\",\"zhangle\":\"Z:\张\乐\"},\"customFields\":{\"project\":\"\所\属\项\目\",\"story\":\"\相\关\需\求\",\"task\":\"\相\关\任\务\",\"pri\":\"\优\先\级\",\"severity\":\"\严\重\程\度\",\"os\":\"\操\作\系\统\",\"browser\":\"\浏\览\器\",\"deadline\":\"\截\止\日\期\",\"mailto\":\"\抄\送\给\",\"keywords\":\"\关\键\词\"},\"showFields\":\"project,story,task,pri,severity,os,browser,deadline,mailto,keywords\",\"productID\":1,\"productName\":\"\数\据\同\步\平\台\",\"moduleOptionMenu\":[\"\\/\"],\"stories\":{\"\":\"\",\"1\":\"1:\同\步\寿\险\看\板\数\据 (\优\先\级:3,\预\计\工\时:0)\"},\"projects\":{\"\":\"\"},\"builds\":{\"trunk\":\"\主\干\"},\"moduleID\":0,\"projectID\":0,\"taskID\":0,\"storyID\":0,\"buildID\":0,\"caseID\":0,\"runID\":0,\"version\":0,\"testtask\":0,\"bugTitle\":\"\",\"pri\":3,\"steps\":\"<p>[\步\骤]<\\/p><br\\/><p>[\结\果]<\\/p><br\\/><p>[\期\望]<\\/p><br\\/>\",\"os\":\"\",\"browser\":\"\",\"projectMembers\":{\"\":\"\",\"baigenhai\":\"B:\白\艮\海\",\"chendong\":\"C:\陈\栋\",\"duyangguang\":\"D:\杜\阳\光\",\"gaojie\":\"G:\高\杰\",\"huangqiaoling\":\"H:\黄\巧\玲\",\"liuliting\":\"L:\刘\莉\婷\",\"liutianlun\":\"L:\刘\天\伦\",\"liuxiaoyu\":\"L:\刘\晓\宇\",\"loujie\":\"L:\娄\洁\",\"luyi\":\"L:\陆\怡\",\"luyuan\":\"L:\陆\远\",\"sunguoliang\":\"S:\孙\国\亮\",\"wangmin\":\"W:\王\旻\",\"wudi\":\"W:\吴\迪\",\"zhangjingwei\":\"Z:\张\景\伟\",\"zhanglei\":\"Z:\张\磊\",\"zhangyunjia\":\"Z:\张\运\佳\",\"admin\":\"A:admin\",\"zhangle\":\"Z:\张\乐\"},\"assignedTo\":\"\",\"deadline\":\"\",\"mailto\":\"\",\"keywords\":\"\",\"severity\":3,\"type\":\"codeerror\",\"branch\":\"0\",\"branches\":[],\"color\":\"\",\"pager\":null}",
    "md5": "027655133369a37ed86b94c398fdbc01"
}