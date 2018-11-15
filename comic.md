## 漫画分销系统

## database

#### comic 漫画

| 字段名 | 类型 | 长度 | 注释 |
| ------ | ------ | ------ | ------ |
| id | int | 11 | 主键 |
| cover | varchar | 255 | 封面 |
| name | varchar | 255 | 名称 |
| author | varchar | 255 | 作者 |
| brief | varchar | 255 | 简介 |
| type_ids | tinyint | 4 | 漫画分类ID（可多选） |
| release_type_id | tinyint | 4 | 发布类型ID (精选漫画、人气漫画、新品上架、热门漫画...) |
| total_chapter | int | 11 | 总章节 |
| free_chapter | int | 11 | 免费章节 |
| pre_chapter_pay | float |  | 章节费用 |
| sort | int | 11 | 排序 |
| heat | int | 11 | 热门度 |
| popularity | int | 11 | 人气数 |
| collection | int | 11 | 收藏数 |
| share_title | varchar | 255 | 分享标题 |
| share_brief | varchar | 255 | 分享简介 |
| spread_times | int | 4 | 推广次数 |
| s_serial | tinyint | 4 | 连载状态（1：连载中 2：已完结） |
| s_fee | tinyint | 4 | 费用（1：收费 2：免费） |
| s_target | tinyint | 4 | 目标用户（1：男频 2：女频） |
| s_space | tinyint | 4 | 篇幅（1：长篇 2：短篇） |
| status | tinyint | 4 | 1：上架 2：下架 |

#### comic_type 漫画类型

| 字段名 | 类型 | 长度 | 注释 |
| ------ | ------ | ------ | ------ |
| id | int | 11 | 主键 |
| comic_type_name | varchar | 255 | 漫画类型 |
| status | tinyint | 4 | 状态 |

#### release_type 发布类型

| 字段名 | 类型 | 长度 | 注释 |
| ------ | ------ | ------ | ------ |
| id | int | 11 | 主键 |
| release_type_name | varchar | 255 | 发布类型 |
| status | tinyint | 4 | 状态 |

#### comic_banner 轮播广告

| 字段名 | 类型 | 长度 | 注释 |
| ------ | ------ | ------ | ------ |
| id | int | 11 | 主键 |
| banner_url | varchar | 255 | 轮播图 |
| jump_url | varchar | 255 | 跳转链接 |
| status | tinyint | 4 | 状态 |

#### comment 评论

| 字段名 | 类型 | 长度 | 注释 |
| ------ | ------ | ------ | ------ |
| id | int | 11 | 主键 |
| comic_id | int | 11 | 漫画id |
| reader_id | int | 11 | 读者id |
| comment_content | varchar | 255 | 评论内容 |
| comment_time | datetime |  | 评论时间 |
| s_show | tinyint | 4 | 显示状态 |
| status | tinyint | 4 | 状态 |

#### reader 读者

| 字段名 | 类型 | 长度 | 注释 |
| ------ | ------ | ------ | ------ |
| id | int | 11 | 主键 |
| proxy_id | int | 11 | 代理ID |
| nickname | varchar | 255 | 昵称 |
| head | varchar | 255 | 头像 |
| balance | float |  | 余额 |
| amount | float |  | 总充值额 |
| registered_time | datetime |  | 注册时间 |
| s_attention | tinyint | 4 | 是否关注 |
| s_vip | tinyint | 4 | 是否vip |
| status | tinyint | 4 | 状态 |

#### consume 消费

| 字段名       | 类型     | 长度 | 注释     |
| ------------ | -------- | ---- | -------- |
| id           | int      | 11   | 主键     |
| openid       | char     | 32   | openid   |
| comic_id     | int      | 11   | 漫画ID   |
| chapter      | int      | 11   | 章节     |
| cost         | float    |      | 花费     |
| consume_time | datetime |      | 消费时间 |



