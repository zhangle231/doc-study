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

#��ȡsession
zentao/api-getsessionid.json

#ʹ���õ���sessinid��¼

zentao/user-login.json?zentaosid=ciq5tbld3sl47dk6ep4a9uvt87
account
password

#����һ������

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
    "data": "{\"title\":\"\��\��\ͬ\��\ƽ\̨::\��Bug\",\"products\":{\"2\":\"\��\��\��\��\",\"1\":\"\��\��\ͬ\��\ƽ\̨\",\"5\":\"\��\��\��\��\",\"4\":\"\��\��\ս\��\",\"3\":\"\��\��\��\��\̨\"},\"users\":{\"\":\"\",\"baigenhai\":\"B:\��\��\��\",\"chendong\":\"C:\��\��\",\"duyangguang\":\"D:\��\��\��\",\"gaojie\":\"G:\��\��\",\"huangqiaoling\":\"H:\��\��\��\",\"liuliting\":\"L:\��\��\��\",\"liutianlun\":\"L:\��\��\��\",\"liuxiaoyu\":\"L:\��\��\��\",\"loujie\":\"L:\¦\��\",\"luyi\":\"L:\½\��\",\"luyuan\":\"L:\½\Զ\",\"sunguoliang\":\"S:\��\��\��\",\"wangmin\":\"W:\��\�F\",\"wudi\":\"W:\��\��\",\"zhangjingwei\":\"Z:\��\��\ΰ\",\"zhanglei\":\"Z:\��\��\",\"zhangyunjia\":\"Z:\��\��\��\",\"admin\":\"A:admin\",\"zhangle\":\"Z:\��\��\"},\"customFields\":{\"project\":\"\��\��\��\Ŀ\",\"story\":\"\��\��\��\��\",\"task\":\"\��\��\��\��\",\"pri\":\"\��\��\��\",\"severity\":\"\��\��\��\��\",\"os\":\"\��\��\ϵ\ͳ\",\"browser\":\"\�\��\��\",\"deadline\":\"\��\ֹ\��\��\",\"mailto\":\"\��\��\��\",\"keywords\":\"\��\��\��\"},\"showFields\":\"project,story,task,pri,severity,os,browser,deadline,mailto,keywords\",\"productID\":1,\"productName\":\"\��\��\ͬ\��\ƽ\̨\",\"moduleOptionMenu\":[\"\\/\"],\"stories\":{\"\":\"\",\"1\":\"1:\ͬ\��\��\��\��\��\��\�� (\��\��\��:3,\Ԥ\��\��\ʱ:0)\"},\"projects\":{\"\":\"\"},\"builds\":{\"trunk\":\"\��\��\"},\"moduleID\":0,\"projectID\":0,\"taskID\":0,\"storyID\":0,\"buildID\":0,\"caseID\":0,\"runID\":0,\"version\":0,\"testtask\":0,\"bugTitle\":\"\",\"pri\":3,\"steps\":\"<p>[\��\��]<\\/p><br\\/><p>[\��\��]<\\/p><br\\/><p>[\��\��]<\\/p><br\\/>\",\"os\":\"\",\"browser\":\"\",\"projectMembers\":{\"\":\"\",\"baigenhai\":\"B:\��\��\��\",\"chendong\":\"C:\��\��\",\"duyangguang\":\"D:\��\��\��\",\"gaojie\":\"G:\��\��\",\"huangqiaoling\":\"H:\��\��\��\",\"liuliting\":\"L:\��\��\��\",\"liutianlun\":\"L:\��\��\��\",\"liuxiaoyu\":\"L:\��\��\��\",\"loujie\":\"L:\¦\��\",\"luyi\":\"L:\½\��\",\"luyuan\":\"L:\½\Զ\",\"sunguoliang\":\"S:\��\��\��\",\"wangmin\":\"W:\��\�F\",\"wudi\":\"W:\��\��\",\"zhangjingwei\":\"Z:\��\��\ΰ\",\"zhanglei\":\"Z:\��\��\",\"zhangyunjia\":\"Z:\��\��\��\",\"admin\":\"A:admin\",\"zhangle\":\"Z:\��\��\"},\"assignedTo\":\"\",\"deadline\":\"\",\"mailto\":\"\",\"keywords\":\"\",\"severity\":3,\"type\":\"codeerror\",\"branch\":\"0\",\"branches\":[],\"color\":\"\",\"pager\":null}",
    "md5": "027655133369a37ed86b94c398fdbc01"
}