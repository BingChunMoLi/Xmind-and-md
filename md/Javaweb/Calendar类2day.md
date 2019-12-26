<!--
 * @Author: 冰彦糖
 * @Date: 2019-12-24 20:32:54
 * @LastEditTime : 2019-12-24 20:38:12
 * @LastEditors  : Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\Javaweb\2day.md
 -->
 ## 构造方法：
 protected Calendar() :由于修饰符是protected，所以无法直接创建该对象。需要通过别的途径生成该对象。
## Calendar类的成员方法
方法|描述
:-:|:-:
static Calendar getInstance()|使用默认时区和区域设置获取日历。通过该方法生成Calendar对象。如下所示：Calendar cr=Calendar.getInstance()；
public void set(int year,int month,int date,int hourofday,int minute,int second)|设置日历的年、月、日、时、分、秒。
public int get(int field)|返回给定日历字段的值。所谓字段就是年、月、日等等。
public void setTime(Date date)|使用给定的Date设置此日历的时间。Date------Calendar
public Date getTime()|返回一个Date表示此日历的时间。Calendar-----Date
abstract void add(int field,int amount)|按照日历的规则，给指定字段添加或减少时间量。
public long getTimeInMillies()|以毫秒为单位返回该日历的时间值。
## 日历字段
1|2|3|4|5|6
:-:|:-:|:-:|:-:|:-:|:-:
YEAR|年|MINUTE|分|DAY_OF_WEEK_IN_MONTH|某月中第几周
MONTH|月|SECOND/MILLISECOND|秒/毫秒|WEEK_OF_MONTH|日历式的第几周
DATE|日|DAY_OF_MONTH|和DATE一样|DAY_OF_YEAR|一年的第多少天
HOUR_OF_DAY|时|DAY_OF_WEEK|周几|WEEK_OF_YEAR|一年的第多少周
原文链接：https://blog.csdn.net/ytasdfg/article/details/81086118