`1.`

![image](https://github.com/chenyime/chenyime.github.io/raw/master/image/5-1.png)

`2.`

![image](https://github.com/chenyime/chenyime.github.io/raw/master/image/5-2.png)

```sql
SET NAMES utf8;
SET FOREIGN_KEY_CHECKS = 0;

-- ----------------------------
--  Table structure for `Hotels`
-- ----------------------------
DROP TABLE IF EXISTS `Hotels`;
CREATE TABLE `Hotels` (
  `id` int(11) NOT NULL,
  `name` varchar(255) NOT NULL,
```

```sql
  `city` varchar(255) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
--  Table structure for `Orders`
-- ----------------------------
DROP TABLE IF EXISTS `Orders`;
CREATE TABLE `Orders` (
  `id` int(11) NOT NULL,
  `userId` int(11) NOT NULL,
  `roomId` int(11) NOT NULL,
  `start` date NOT NULL,
  `end` date NOT NULL,
  PRIMARY KEY (`id`),
  KEY `roomId` (`roomId`),
  CONSTRAINT `roomId` FOREIGN KEY (`roomId`) REFERENCES `Rooms` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
--  Table structure for `Rooms`
-- ----------------------------
DROP TABLE IF EXISTS `Rooms`;
CREATE TABLE `Rooms` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  `cost` decimal(10,0) NOT NULL,
  `hotelId` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `hotelId` (`hotelId`),
  CONSTRAINT `hotelId` FOREIGN KEY (`hotelId`) REFERENCES `Hotels` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

SET FOREIGN_KEY_CHECKS = 1;
```

`3.`

> 简述 领域模型 在项目开发中的作用

领域模型设计是需求分析的关键步骤。它帮助用户及需求分析人员建立业务概念，确定用户业务的问题域，系统涉及的业务范围等等。

> 简述 数据库模型 与 领域模型 的差异

领域模型是一个尽可能贴近真实流程的模型，是基于需求驱动的，不关心与需求无关的，如数据保存等。

> 假设你主导软件数据设计评审，你认为需要哪些准备文档，会关注哪些要素（不能超过 5 个）。百度哦！

需求分析文档、软件设计文档、数据库设计文档

要素：

1. 设计是否满足软件设计的一般要求
2. 表结构是否合理
3. 是否遵循统一的命名规范
