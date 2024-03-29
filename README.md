-- ----------------------------
-- Table structure for ad
-- ----------------------------
DROP TABLE IF EXISTS `ad`;
CREATE TABLE `ad` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '主键',
  `title` varchar(50) DEFAULT NULL COMMENT '标题',
  `img_file_name` varchar(100) DEFAULT NULL COMMENT '图片文件名',
  `link` varchar(200) DEFAULT NULL COMMENT '链接地址',
  `weight` int(11) DEFAULT NULL COMMENT '权重',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for business
-- ----------------------------
DROP TABLE IF EXISTS `business`;
CREATE TABLE `business` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '主键',
  `img_file_name` varchar(100) DEFAULT NULL COMMENT '图片文件名',
  `title` varchar(50) DEFAULT NULL COMMENT '标题',
  `subtitle` varchar(100) DEFAULT NULL COMMENT '副标题',
  `price` decimal(11,2) DEFAULT NULL COMMENT '价格(单位：元)',
  `distance` int(11) DEFAULT NULL COMMENT '距离(单位：米)',
  `number` int(11) DEFAULT NULL COMMENT '已售数量',
  `desc` varchar(500) DEFAULT NULL COMMENT '描述',
  `city` varchar(16) DEFAULT NULL COMMENT '城市',
  `category` varchar(16) DEFAULT NULL COMMENT '类别',
  `star_total_num` int(11) DEFAULT NULL COMMENT '评论星星总数',
  `comment_total_num` int(11) DEFAULT NULL COMMENT '评论总次数',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for comment
-- ----------------------------
DROP TABLE IF EXISTS `comment`;
CREATE TABLE `comment` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '主键',
  `orders_id` int(11) DEFAULT NULL COMMENT '用户名',
  `comment` varchar(500) DEFAULT NULL COMMENT '评论内容',
  `star` int(1) DEFAULT NULL COMMENT '星级评分',
  `create_time` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `Normal_create_time` (`create_time`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for dic
-- ----------------------------
DROP TABLE IF EXISTS `dic`;
CREATE TABLE `dic` (
  `type` varchar(16) NOT NULL,
  `code` varchar(16) NOT NULL,
  `name` varchar(16) NOT NULL,
  `weight` int(11) DEFAULT NULL,
  PRIMARY KEY (`type`,`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for member
-- ----------------------------
DROP TABLE IF EXISTS `member`;
CREATE TABLE `member` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `phone` bigint(13) DEFAULT NULL COMMENT '手机号',
  `name` varchar(16) DEFAULT NULL COMMENT '用户名',
  `password` char(32) DEFAULT NULL COMMENT '密码',
  PRIMARY KEY (`id`),
  UNIQUE KEY `phone_unique` (`phone`),
  UNIQUE KEY `name_unique` (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for orders
-- ----------------------------
DROP TABLE IF EXISTS `orders`;
CREATE TABLE `orders` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '主键',
  `business_id` int(11) DEFAULT NULL COMMENT '商户主键',
  `member_id` int(11) DEFAULT NULL COMMENT '会员主键',
  `num` int(11) DEFAULT NULL COMMENT '消费人数',
  `comment_state` int(1) DEFAULT NULL COMMENT '评论状态 -- 0：未评论 2：已评论',
  `price` decimal(11,2) DEFAULT NULL COMMENT '价格(消费金额)',
  `create_time` datetime DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for sys_action
-- ----------------------------
DROP TABLE IF EXISTS `sys_action`;
CREATE TABLE `sys_action` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(20) DEFAULT NULL COMMENT '动作名称',
  `url` varchar(200) DEFAULT NULL COMMENT '动作地址',
  `menu_id` int(11) DEFAULT NULL,
  `method` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='系统表-操作表，权限拦截用，存放系统里全部动作。';


-- ----------------------------
-- Table structure for sys_menu
-- ----------------------------
DROP TABLE IF EXISTS `sys_menu`;
CREATE TABLE `sys_menu` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(64) DEFAULT NULL,
  `url` varchar(256) DEFAULT NULL,
  `parent_id` int(11) DEFAULT NULL,
  `order_num` decimal(5,0) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for sys_group
-- ----------------------------
DROP TABLE IF EXISTS `sys_group`;
CREATE TABLE `sys_group` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(32) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for sys_group_action
-- ----------------------------
DROP TABLE IF EXISTS `sys_group_action`;
CREATE TABLE `sys_group_action` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `group_id` int(11) DEFAULT NULL,
  `action_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for sys_group_menu
-- ----------------------------
DROP TABLE IF EXISTS `sys_group_menu`;
CREATE TABLE `sys_group_menu` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `group_id` int(11) DEFAULT NULL,
  `menu_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


-- ----------------------------
-- Table structure for sys_param
-- ----------------------------
DROP TABLE IF EXISTS `sys_param`;
CREATE TABLE `sys_param` (
  `param_key` varchar(20) DEFAULT NULL,
  `param_value` datetime DEFAULT NULL,
  `param_desc` varchar(200) DEFAULT NULL,
  UNIQUE KEY `Unique_key` (`param_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='系统参数表';


-- ----------------------------
-- Table structure for sys_user
-- ----------------------------
DROP TABLE IF EXISTS `sys_user`;
CREATE TABLE `sys_user` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '用户id',
  `name` varchar(32) NOT NULL COMMENT '用户名',
  `password` varchar(32) NOT NULL COMMENT '登录密码',
  `ch_name` varchar(32) DEFAULT NULL,
  `group_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `Unique_name` (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of ad
-- ----------------------------
INSERT INTO `ad` VALUES ('1', '暑假5折', '1495353501938_ad_1.png', 'http://www.atguigu.com', '6');
INSERT INTO `ad` VALUES ('2', '特价出国', '1495353568008_ad_2.png', 'http://www.atguigu.com', '5');
INSERT INTO `ad` VALUES ('3', '亮亮车', '1495353623949_ad_3.png', 'http://www.atguigu.com', '4');
INSERT INTO `ad` VALUES ('4', '学钢琴', '1495353664627_ad_4.png', 'http://www.atguigu.com', '3');
INSERT INTO `ad` VALUES ('5', '电影', '1495353700766_ad_5.png', 'http://www.atguigu.com', '2');
INSERT INTO `ad` VALUES ('6', '旅游热线', '1495353735839_ad_6.png', 'http://www.atguigu.com', '1');


-- ----------------------------
-- Records of business
-- ----------------------------
INSERT INTO `business` VALUES ('1', '1495354718489_business_1.png', '汉堡大大', '叫我汉堡大大，还你多彩口味', '28.00', '120', '0', '1、当图片在app上不显示时，请查看system.properties里的访问路径，保存路径，如果看懂了视频：\r\n应该知道这个配置文件里的参数怎么改、我给你们的图片放在哪就可以了。<br/>2、后台管理用户名密码：admin/admin<br/>3、如果出现“没有权限访问请求资源，请切换账户后重试！”，请不要着急，先把applicationContext-web.xml中关于AuthInterceptor拦截器部分注释掉，等把拦截器听懂再来看看怎么回事！', '北京', 'meishi', '0', '0');


-- ----------------------------
-- Records of dic
-- ----------------------------
INSERT INTO `dic` VALUES ('category', 'jiehun', '结婚', '4');
INSERT INTO `dic` VALUES ('category', 'jingdian', '景点', '1');
INSERT INTO `dic` VALUES ('category', 'ktv', 'KTV', '2');
INSERT INTO `dic` VALUES ('category', 'meishi', '美食', '3');
INSERT INTO `dic` VALUES ('city', '上海', '上海', '2');
INSERT INTO `dic` VALUES ('city', '北京', '北京', '1');
INSERT INTO `dic` VALUES ('city', '广州', '广州', '3');
INSERT INTO `dic` VALUES ('httpMethod', 'DELETE', 'DELETE', '2');
INSERT INTO `dic` VALUES ('httpMethod', 'GET', 'GET', '4');
INSERT INTO `dic` VALUES ('httpMethod', 'POST', 'POST', '1');
INSERT INTO `dic` VALUES ('httpMethod', 'PUT', 'PUT', '3');


-- ----------------------------
-- Records of member
-- ----------------------------
INSERT INTO `member` VALUES ('1', '13912345678', null, null);


-- ----------------------------
-- Records of sys_menu
-- ----------------------------
INSERT INTO `sys_menu` VALUES ('1', '系统管理', '', '0', '1');
INSERT INTO `sys_menu` VALUES ('2', '权限管理', '/auth', '1', '1');
INSERT INTO `sys_menu` VALUES ('3', '内容管理', '', '0', '2');
INSERT INTO `sys_menu` VALUES ('4', '广告管理', '/ad', '3', '1');
INSERT INTO `sys_menu` VALUES ('5', '商户管理', '/businesses', '3', '2');
INSERT INTO `sys_menu` VALUES ('6', '评论查询', '/comments', '3', '3');
INSERT INTO `sys_menu` VALUES ('7', '订单查询', '/orders', '3', '4');
INSERT INTO `sys_menu` VALUES ('8', '统计报表', '', '0', '3');
INSERT INTO `sys_menu` VALUES ('9', '订单统计', '/orderReport', '8', '1');


-- ----------------------------
-- Records of sys_action
-- ----------------------------
INSERT INTO `sys_action` VALUES ('1', '浏览', '/auth', '2', '');
INSERT INTO `sys_action` VALUES ('2', '浏览用户', '/users', '2', '');
INSERT INTO `sys_action` VALUES ('3', '维护用户', '/users/.{1,}', '2', '');
INSERT INTO `sys_action` VALUES ('4', '浏览用户组', '/groups', '2', '');
INSERT INTO `sys_action` VALUES ('5', '维护用户组', '/groups/.{1,}', '2', '');
INSERT INTO `sys_action` VALUES ('6', '分配菜单', '/groups/.{1,}/menus', '2', '');
INSERT INTO `sys_action` VALUES ('7', '浏览菜单', '/menus', '2', '');
INSERT INTO `sys_action` VALUES ('8', '维护菜单', '/menus/.{1,}', '2', '');
INSERT INTO `sys_action` VALUES ('9', '菜单排序', '/menus/.{1,}/.{1,}/.{1,}', '2', '');
INSERT INTO `sys_action` VALUES ('10', '浏览动作', '/actions', '2', '');
INSERT INTO `sys_action` VALUES ('11', '维护动作', '/actions/.{1,}', '2', '');

INSERT INTO `sys_action` VALUES ('12', '浏览', '/ad', '4', '');
INSERT INTO `sys_action` VALUES ('13', '查询', '/ad/search', '4', '');
INSERT INTO `sys_action` VALUES ('14', '删除', '/ad/remove', '4', '');
INSERT INTO `sys_action` VALUES ('15', '新增页初始化', '/ad/addInit', '4', '');
INSERT INTO `sys_action` VALUES ('16', '新增', '/ad/add', '4', '');
INSERT INTO `sys_action` VALUES ('17', '修改页初始化', '/ad/modifyInit', '4', '');
INSERT INTO `sys_action` VALUES ('18', '修改', '/ad/modify', '4', '');

INSERT INTO `sys_action` VALUES ('19', '浏览', '/businesses', '5', 'GET');
INSERT INTO `sys_action` VALUES ('20', '删除', '/businesses/.{1,}', '5', 'DELETE');
INSERT INTO `sys_action` VALUES ('21', '新增页初始化', '/businesses/addPage', '5', 'GET');
INSERT INTO `sys_action` VALUES ('22', '新增', '/businesses', '5', 'POST');
INSERT INTO `sys_action` VALUES ('23', '修改页初始化', '/businesses/.{1,}', '5', 'GET');
INSERT INTO `sys_action` VALUES ('24', '修改', '/businesses/.{1,}', '5', 'PUT');

INSERT INTO `sys_action` VALUES ('25', '浏览', '/orderReport', '9', '');
INSERT INTO `sys_action` VALUES ('26', '统计', '/orderReport/count', '9', 'GET');

-- ----------------------------
-- Records of sys_group
-- ----------------------------
INSERT INTO `sys_group` VALUES ('1', '系统管理员');
INSERT INTO `sys_group` VALUES ('2', '管理');
INSERT INTO `sys_group` VALUES ('3', '业务');


-- ----------------------------
-- Records of sys_group_action
-- ----------------------------
INSERT INTO `sys_group_action` VALUES ('1', '1', '1');
INSERT INTO `sys_group_action` VALUES ('2', '1', '2');
INSERT INTO `sys_group_action` VALUES ('3', '1', '3');
INSERT INTO `sys_group_action` VALUES ('4', '1', '4');
INSERT INTO `sys_group_action` VALUES ('5', '1', '5');
INSERT INTO `sys_group_action` VALUES ('6', '1', '6');
INSERT INTO `sys_group_action` VALUES ('7', '1', '7');
INSERT INTO `sys_group_action` VALUES ('8', '1', '8');
INSERT INTO `sys_group_action` VALUES ('9', '1', '9');
INSERT INTO `sys_group_action` VALUES ('10', '1', '10');
INSERT INTO `sys_group_action` VALUES ('11', '1', '11');
INSERT INTO `sys_group_action` VALUES ('12', '1', '12');
INSERT INTO `sys_group_action` VALUES ('13', '1', '13');
INSERT INTO `sys_group_action` VALUES ('14', '1', '14');
INSERT INTO `sys_group_action` VALUES ('15', '1', '15');
INSERT INTO `sys_group_action` VALUES ('16', '1', '16');
INSERT INTO `sys_group_action` VALUES ('17', '1', '17');
INSERT INTO `sys_group_action` VALUES ('18', '1', '18');
INSERT INTO `sys_group_action` VALUES ('19', '1', '19');
INSERT INTO `sys_group_action` VALUES ('20', '1', '20');
INSERT INTO `sys_group_action` VALUES ('21', '1', '21');
INSERT INTO `sys_group_action` VALUES ('22', '1', '22');
INSERT INTO `sys_group_action` VALUES ('23', '1', '23');
INSERT INTO `sys_group_action` VALUES ('24', '1', '24');
INSERT INTO `sys_group_action` VALUES ('25', '1', '25');
INSERT INTO `sys_group_action` VALUES ('26', '1', '26');


-- ----------------------------
-- Records of sys_group_menu
-- ----------------------------
INSERT INTO `sys_group_menu` VALUES ('1', '1', '1');
INSERT INTO `sys_group_menu` VALUES ('2', '1', '2');
INSERT INTO `sys_group_menu` VALUES ('3', '1', '3');
INSERT INTO `sys_group_menu` VALUES ('4', '1', '4');
INSERT INTO `sys_group_menu` VALUES ('5', '1', '5');
INSERT INTO `sys_group_menu` VALUES ('6', '1', '6');
INSERT INTO `sys_group_menu` VALUES ('7', '1', '7');
INSERT INTO `sys_group_menu` VALUES ('8', '1', '8');
INSERT INTO `sys_group_menu` VALUES ('9', '1', '9');


-- ----------------------------
-- Records of sys_param
-- ----------------------------
INSERT INTO `sys_param` VALUES ('last_sync_star_time', null, '最后一次同步星星数时间');


-- ----------------------------
-- Records of sys_user
-- ----------------------------
INSERT INTO `sys_user` VALUES ('1', 'admin', '21232f297a57a5a743894a0e4a801fc3', '超级管理员', '1');
INSERT INTO `sys_user` VALUES ('2', 'zhangsan', '01d7f40760960e7bd9443513f22ab9af', '张三', null);
INSERT INTO `sys_user` VALUES ('3', 'lisi', 'dc3a8f1670d65bea69b7b65048a0ac40', '李四', null);
