#drools������Ŀ
drools��һ�����java���ԵĹ������棬��������ֻ�����е�һ���֣�����drools��������5��ģ�飬�ֱ�Ϊ��
+ Drools Engine
+ Drools and jBPM integration
+ Business Central Workbench
+ Drools and jBPM tools
+ KIE Execution Server

����drools engineΪ��������沿�֣�����Ϊ����չ�Ĳ��֣����ǲ�����˵�����Ͳ���Ҫ�������������������Ľ����������ѡ������Ʒ�Ĺؼ���

���Ƕ��ڳ�ѧ����������ô���Ĳ�Ʒ������������ȴ�����������뻹�Ǵ���򵥵���Ŀʹ�ÿ�ʼ���ţ�������һ����õĳ���Ϊ��������һ��drools�ļ�ʹ�á�

drools�Դ����Ż���Ǹ����Ӿͺܺã���Ҳ�����Ϊ��˵��һ�£����ȳ����������ġ������¼���ʵ�壺
+ ����
+ ��ˮ��
+ ����
+ �Ż�

��������һ�����ǵĹ�ϵ��
+ ��������Ż��˾ͷ�����
+ ������������ˮ��
+ �����˾͹ر���ˮ��

����ռ�ڹ���ĽǶ�����������⣬���ǿ��԰������Ϊ��������ˮ���Ĺ�ϵ����Ϊ���¹���
+ �б���
+ û����
+ ��ˮ��
+ ��ˮ��

��drools����Ĺ���Ϊwhen...then...end����ʽ��ÿ�����򶼷�������ģ�壬����ָ��������ִ���߼����������ǿ�һ������Ż�ľ���Ĺ���

```
rule RaiseAlarm 
when
     exists Fire()
then
    insert( new Alarm( "house1" ) );
end
```

����rule RaiseAlarm˵���˹�������ƣ�RaiseAlarmΪ�������ơ�

exists Fire()�ǹ��򴥷�������������һ��Fire�����ʱ���򴥷��������

insert(new Alarm( "house1" )); �ǹ���ľ���ִ���߼ӣ�����һ��Fire����ʱ���´���һ��Alarm���󣬲��������Ĺ��������С�

���˾����������������ƺͿ�����

Ȼ����Ҫ�����������java������ִ�С���������������������������û��������������Ļ�����

##���������

��maven��ĿΪ�����������°����ɡ�

```
		<dependency>
			<groupId>org.kie</groupId>
			<artifactId>kie-api</artifactId>
		</dependency>
		<dependency>
			<groupId>org.drools</groupId>
			<artifactId>drools-compiler</artifactId>
			<scope>runtime</scope>
		</dependency
```

##���û���

drools�������ļ�Ϊkmodule.xml�ļ������ļ���Ҫ����META-INFĿ¼�²�����Ч��

������xml�ľ�����������Ҫ��Ϊ�����㼶��kmodule->kbase->ksession��kbase����������Ӧ·���µĹ���ksession���ڽ�������Ĺ���ִ��session��

```
<kmodule>
	<kbase packages="org...">
		<ksession name="FireLogicalKS" />
	</kbase>
</kmodule>
```

##���������Ļ���

��java��main�����й�����ͨ��ksession������ִ�й����߼��ġ�����Ĺ������£�

```
	KieContainer kc = KieServices.Factory.get().getKieClasspathContainer();
	KieSession ksession = kc.newKieSession("FireLogicalKS");
	ksession.fireAllRules()
```

��������������Ĺ����ú����ǻ�Ҫ��� һ��fact��fact���Ǿ���Ķ�����������ֻ�ǽ�����һ������ģ�ͣ�ֻ�ǳ���ĸ�����Ƕ����˷��ӣ�����ʵ�Hִ�й����ʱ����û�з��ӵģ���Ӧ���Ǿ����ÿһ�䷿�ӣ�������ʵ��һ��������һ�����ҵȵ� ��������Ҫͨ�����·�������һ������ʵ�Ķ��������������������Ķ���

```
	Room room = new Room(name);
	ksession.insert(room)
```

ͨ�����ϵĴ���Ϳ��Կ�ʼ�����ˣ��������û�д����������������ô�ǲ���������ӳ�ģ�����������Ҫ���һ���¼��������������������������Ҫ��һ�»𣬹���һ��Fire���󣬷������£�

```
	Fire kitchenFire = new Fire(name2room.get("kitchen"));
	FactHandle kitchenFireHandle = ksession.insert(kitchenFire);
```

���ھͿ��Կ��������ִ��Ч���ˣ�ͨ�����ϵ�˵����drools�ļ�ʹ�þ�����ˡ���Ϊ���õ���7.3Ŀǰ���µİ汾�������ϰ汾�Ľ��ܱȽ϶࣬��������°汾�ı仯����ͦ��ģ�ϣ��������������

