
angularjs中的filter(过滤器)——格式化日期的date

date过滤器的功能是基于要求的格式格式化一个日期成为一个字符串。

格式化字符串的基本参数：

‘yyyy’: 用4位数字表示年（例如：AD 1 => 0001, AD 2010 => 2010）

‘yy’: 用两位数字表示年（00-99）（例如：AD 2001 => 01, AD 2010 => 10）

‘y’: 用一位数字代表年（例如：AD 1 => 1, AD 199 => 199）

‘MMMM’: 英文全称表示月（January-December）

‘MMM’: 英文缩写表示月（Jan-Dec）

‘MM’: 两位数字表示月（01-12）

‘M’: 月（1-12）

‘dd’: 两位数字表示日（01-31）

‘d’: 日（1-31）

‘EEEE’: 英文全称的一周中的天（Sunday-Saturday）

‘EEE’: 英文缩写的一周中的天（Sun-Sat）

‘HH’: 两位数表示24小时制的时（00-23）

‘H’: 24小时制的时（0-23）

‘hh’: 两位数字表示上午或下午的时（01-12）

‘h’: 上午或下午的时（1-12）

‘mm’: 两位数字表示分（00-59）

‘m’: 分（0-59）

‘ss’: 两位数字表示秒（00-59）

‘s’: 秒（0-59）

‘sss’: 毫秒（000-999）

‘a’: AM/PM

‘Z’: 4位数字（+符号）代表时区偏移量（-1200——+1200）

‘ww’: 用两位数字表示一年的周数（00-53），第一周（01）是一年中的第一个星期四

‘w’:  一年的周数(0-53)，第一周（1）是一年中的第一个星期四

‘G’,’GG’,‘GGG’: 年代字符串的缩写形式，例如‘AD’（公元）

‘GGGG’: 年代字符串的全称，例如‘Anno Domini’（公元）

上面这些参数我们可以根据自己的意愿自由组合得到自己想要的格式，例如'yyyy-MM-dd'等。

 

格式化字符串也提供了一些预定义的本地化格式，可以方便我们使用：

medium：‘MMM d,y h:mm:ss a’ 例如：Sep 3, 2010 12:05:08 PM

short：‘M/d/yy h:mm a’ 例如： 9/3/10 12:05 PM

fullDate: ’EEEE,MMMM d,y’ 例如：Friday, September 3, 2010

longDate: ‘MMMM d,y’ 例如：September 3, 2010

mediumDate: ’MMM d,y’ 例如： Sep 3, 2010

shortDate: ’M/d/y’ 例如： 9/3/10

mediumTime: ’h:mm:ss a’ 例如：12:05:08 PM

shortTime: ’h:mm a’  例如：12:05 PM

格式化字符串可以包含文本值。这些需要被单引号包围（例如 “h ‘in the morning’”）,如果想输出一对单引号，就在一个序列中用两个双引号（例如：“h ‘o’’clock’”）

 

date过滤器的用法：

1.在html中用法：{{ date_expression | date : format : timezone}}

实例：

<span>{{1288323623006 | date:'medium'}}</span><br>

 <span>{{1288323623006 | date:'yyyy-MM-dd HH:mm:ss Z'}}</span><br>

<span>{{'1288323623006' | date:'MM/dd/yyyy @ h:mma'}}</span><br>

<span>{{'1288323623006' | date:"MM/dd/yyyy 'at' h:mma"}}</span><br>

输出结果为：

 Oct 29, 2010 11:40:23 AM

 2010-10-29 11:40:23 +0800

10/29/2010 @ 11:40AM

10/29/2010 at 11:40AM

2.在javascript中的用法：$filter('date')(date, format, timezone)

实例：

var today = new Date();
$scope.formatDate = $filter('date')(today, 'yyyy-MM-dd');

输出结果为：

2015-01-28