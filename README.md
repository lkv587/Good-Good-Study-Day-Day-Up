
# 常用开发工具

	* idea https://www.cnblogs.com/iathanasy/p/9469280.html 永久激活
	
	* mysql (sqlyog)
	
	* git	
	
	* xshell
	
	* xmind
	
	* evething
	
	* google
	
	* postman
	
	* ftp  FlashFxp
	
	* notepad++
	
	* youdao
	
	* clover
	
* Nothing is imporsibel,Just do it!	sekai ni itami o-sin la ten se		世界（せかい）に痛（いた）みを 神罗天征（しんらてんせい）

* 我不是天生强大，而是天生要强！
干柿鬼鲛：力量宇智波鼬：亲情迪达拉：艺术蝎：青春飞段：宗教角都：金钱小南：友情漩涡长门：和平绝：自由宇智波带土：爱情

# 常用Linux命令
	ssh bus-coll.01.tomcat.prod.uc
	-- logs
	log_mobanker-collection-api
	vi /opt/tomcat8/logs/catalina_ln.out
	docker ps|grep business
	docker exec -it convoy_jsystem_business /bin/bash
	yum clean all
	yum list|grep xxx
	yum install xxx	
	--tomcat
	/etc/init.d/tomcat8/stop
	/etc/init.d/tomcat8/start
	--Netty restart
	service mobanker-message-api restart
	-- logs
	tail -f /opt/tomcat7/logs/catalina_ln.out
	cat jeewx-2015-09-20.log | grep 验证码
	vi catalina_ln.out
	/ sendMsg n
	? sendMsg n
	:wq 保存退出
	:q! 强制退出
	#H5服务启动
	/etc/init.d/httpd start
	
# idea 激活(2018年8月3日14:44:07)
	http://active.chinapyg.com/  //失效
	http://idea.toocruel.net  //在用
	https://www.cnblogs.com/iathanasy/p/9469280.html 永久激活方法
	
# Git git@192.168.1.206:root/mobanker-collection.git 	
# idea 快捷键
	ctrl+alt+s 设置
	ctrl+shift+a  搜索
	ctrl+alt+h 查找方法被哪些地方调用 alt+f7 也可以作用在变量上，列出某个类里，哪些地方使用了该变量
	ctrl+shift+enter 表示为您收尾的意思
	ctrl+shift+alt+n 使用symbol来查找
	ctrl+z 撤销  ctrl+shift+z 反撤销
	ctrl+z 打开最近文件
# Mybatis.xml	
	<if test="userName!=null and userName != ''">
		AND user_name LIKE "%"#{userName}"%"
	</if>
	 and assign_areas like CONCAT('%','${assignAreas}','%' )
	<if test="beginAccount!=null">
		<![CDATA[ and account>=#{beginAccount}]]>
	</if>
	merchant_name like concat (#{merchantName},'%')	
	
	<if test="afterOverdue!=null">
	<if test="afterOverdue==1">
		and late_days > 0
	</if>
	<if test="afterOverdue==0">
		AND <![CDATA[ late_days <=0 ]]>
	</if>
	<foreach collection="ids" item="item" open="(" close=")" separator=",">
		#{item}
	</foreach>

# Java日期转换	
	Date d = new Date();  
	SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");  
	String dateNowStr = sdf.format(d);
	JAVA8
	#时间戳
	Instant timestamp = Instant.now();
	#当前日期
	LocalDate now = LocalDate.now();
	#日期转换
	LocalDateTime arrivalDate  = LocalDateTime.now();
	DateTimeFormatter format = DateTimeFormatter.ofPattern("MMMdd yyyy  hh:mm a");
    String landing = arrivalDate.format(format);
	//Date转换为LocalDateTime 
	public static LocalDateTime convertDateToLDT(Date date) {
		return LocalDateTime.ofInstant(date.toInstant(), ZoneId.systemDefault()); 
	}
	//LocalDateTime转换为Date 
	public static Date convertLDTToDate(LocalDateTime time) {	
		return Date.from(time.atZone(ZoneId.systemDefault()).toInstant()); 	
	}
	#转换
	if (StringUtils.isNotEmpty(teamId)) {
		teamIds = Arrays.asList(teamId.split(","));
	}
	#JSON转换
	List<AssignCollector> assignCollectors = JSON.parseArray(overdueTaskBo.getAssignInfos(),AssignCollector.class);
	#logger
	private Logger logger = LoggerFactory.getLogger(this.getClass());
	
# 清缓存命令
	cmd-->ipconfig/flushdns
# MYSQL编码
	如果你在使用MySQL或MariaDB，不要用“utf8”编码，改用“utf8mb4，主库GBK，其他UTF-8
# http请求
	JSONObject jstr = HttpClientUtil.getBusinessUrl(url,"post", map);
	
# java异常处理

	/**
	 * 业务受理失败异常
	 */
	public class ServiceException extends RuntimeException {
	//接收reason参数用来描述业务失败原因.
	public ServiceException(String reason) {  super(reason); }
	}
	
	/**
	* 修改用户信息
	* @param user 要修改的用户数据
	*/
	public void updateUser(User user) {
	User userOrig = userDao.getUserById(user.getUserID());
	if (null == userOrig) {
	  throw new ServiceException("用户不存在");
	}
	if (userOrig.isLocked()) {
	  throw new ServiceException("用户被锁定,不允许修改");
	}
	if (!user.getVersion().equals(userOrig.getVersion())) {
	  throw new ServiceException("用户已经被别人修改过,请刷新重试");
	}
	// TODO 保存用户数据  ... 
	}
	@ControllerAdvice(basePackages = { "com.xxx.xxx.bussiness.xxx" })
	public class ModuleControllerAdvice {
	private static final Logger LOGGER = LoggerFactory.getLogger(ModuleControllerAdvice.class);
	private static final Logger SERVICE_LOGGER = LoggerFactory.getLogger(ServiceException.class);
	
	/**
	* 业务受理失败
	*/
	@ResponseBody
	@ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR)
	@ExceptionHandler(ServiceException.class)
	private JSONResult handleServiceException(ServiceException exception) {
	String message = "业务受理失败,原因:" + exception.getLocalizedMessage();
	SERVICE_LOGGER.info(message);
	JSONResult json = new JSONResult();
	json.serCode(500001); // 500000表示系统异常,500001表示业务逻辑异常
	json.setMessage(message); 
	return json;
	}
	}  
	#对象空判断
	/**
	* 判断对象为空
	* 
	* @param obj
	*            对象名
	* @return 是否为空
	*/
	@SuppressWarnings("rawtypes")
	public static boolean isEmpty(Object obj)
	{
	if (obj == null)
	{
		return true;
	}
	if ((obj instanceof List))
	{
		return ((List) obj).size() == 0;
	}
	if ((obj instanceof String))
	{
		return ((String) obj).trim().equals("");
	}
	return false;
	}

	/**
	* 判断对象不为空
	* 
	* @param obj
	*            对象名
	* @return 是否不为空
	*/
	public static boolean isNotEmpty(Object obj)
	{
	return !isEmpty(obj);
	}

* List<String> userIdList = Arrays.asList(cbi.getUserIds().split(","));
	
* redies命名 产线:服务:方法名
	
* UUID.randomUUID().toString().trim().replaceAll("-","")	

* Idea 配置Git https://blog.csdn.net/u010348570/article/details/81204371?utm_source=blogxgwz0
	ssh-keygen -t rsa -C 'likang@mobanker.com'  

* Raft算法动画演示地址 http://thesecretlivesofdata.com/raft/

# Logger 日志
	import org.slf4j.Logger;
	import org.slf4j.LoggerFactory;
	private Logger logger = LoggerFactory.getLogger(this.getClass());
	
	
