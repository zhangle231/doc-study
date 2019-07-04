#drools建立项目
drools是一款基于java语言的规则引擎，但是引擎只是其中的一部分，整个drools包括以下5个模块，分别为：
+ Drools Engine
+ Drools and jBPM integration
+ Business Central Workbench
+ Drools and jBPM tools
+ KIE Execution Server

其中drools engine为其规则引擎部分，其它为其扩展的部分，但是并不是说其它就不重要，而正是由于其完整的解决方案才是选择这款产品的关键。

但是对于初学者来讲，这么宠大的产品还是让人望而却步，所以我想还是从最简单的项目使用开始入门，下面以一个最好的场景为例，讲解一下drools的简单使用。

drools自带的着火的那个例子就很好，我也以这个为例说明一下，首先场景是这样的。有以下几个实体：
+ 房间
+ 洒水器
+ 报警
+ 着火

接下来看一下它们的关系：
+ 房间如果着火了就发报警
+ 报警想起后打开洒水器
+ 火灭了就关闭洒水器

但是占在规则的角度来看这个问题，我们可以把问题简化为报警和洒水器的关系。变为以下规则：
+ 有报警
+ 没报警
+ 洒水开
+ 洒水关

而drools抽象的规则为when...then...end的形式。每条规则都符合以上模板，即在指定条件下执行逻辑。下面我们看一个监控着火的具体的规则：

```
rule RaiseAlarm 
when
     exists Fire()
then
    insert( new Alarm( "house1" ) );
end
```

首先rule RaiseAlarm说是了规则的名称，RaiseAlarm为规则名称。

exists Fire()是规则触发的条件，当有一个Fire对象的时候，则触发这个规则。

insert(new Alarm( "house1" )); 是规则的具体执行逻加，当有一个Fire对象时，新创建一个Alarm对象，并将其加入的规则引擎中。

至此就完成了这个规则的设计和开发。

然后，需要将这个规则在java程序中执行。这块包含三部，加入包依赖，配置环境，构建上下文环境。

##加入包依赖

以maven项目为例，加入如下包即可。

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

##配置环境

drools的配置文件为kmodule.xml文件，该文件需要放在META-INF目录下才能生效。

以下是xml的具体样例，主要分为三个层级，kmodule->kbase->ksession，kbase用于搜索对应路径下的规则。ksession用于建立具体的规则执行session。

```
<kmodule>
	<kbase packages="org...">
		<ksession name="FireLogicalKS" />
	</kbase>
</kmodule>
```

##构建上下文环境

在java的main函数中规则是通过ksession对象来执行规则逻辑的。建造的过程如下：

```
	KieContainer kc = KieServices.Factory.get().getKieClasspathContainer();
	KieSession ksession = kc.newKieSession("FireLogicalKS");
	ksession.fireAllRules()
```

规则引擎的上下文构建好后，我们还要添加 一下fact。fact就是具体的对象，上面我们只是建立了一个规则模型，只是抽象的概念。我们定义了房子，但是实際执行规则的时候是没有房子的，而应该是具体的每一间房子，比如真实的一个厨房，一个卧室等等 。我们需要通过以下方法创建一个个真实的对象。这个才是真正规则处理的对象。

```
	Room room = new Room(name);
	ksession.insert(room)
```

通过以上的代码就可以开始规则了，但是如果没有触发规则的条件，那么是不会有任务反映的，所以我们需要添加一下事件。用来触发规则，这里就是我们要放一下火，构建一个Fire对象，方法如下：

```
	Fire kitchenFire = new Fire(name2room.get("kitchen"));
	FactHandle kitchenFireHandle = ksession.insert(kitchenFire);
```

现在就可以看到规则的执行效果了，通过以上的说明，drools的简单使用就完成了。因为我用的是7.3目前最新的版本，网上老版本的介绍比较多，但是这个新版本的变化还是挺大的，希望能有所帮助。

