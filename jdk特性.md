# time

Instant 类代表的是某个时间（有点像 java.util.Date），准确的说是：”是不带时区的即时时间点“，它是精确到纳秒的（而不是象旧版本的Date精确到毫秒）。如果使用纳秒去表示一个时间则原来使用一位Long类型是不够的，需要占用更多一点的存储空间，实际上其内部是由两个Long字段组成，第一个部分保存的是自标准Java计算时代（就是1970年1月1日开始）到现在的秒数，第二部分保存的是纳秒数（永远不会超过999,999,999）。

LocalDateTime
它表示的是不带时区的 日期及时间，替换之前的Calendar。看上去，LocalDateTime和Instant很象，但记得的是“Instant中是不带时区的即时时间点。可能有人说，即时的时间点 不就是日期＋时间么？看上去是这样的，但还是有所区别，比如LocalDateTime对于用户来说，可能就只是一个简单的日期和时间的概念，考虑如下的 例子：两个人都在2013年7月2日11点出生，第一个人是在英国出生，而第二个是在加尼福利亚，如果我们问他们是在什么时候出生的话，则他们看上去都是 在同样的时间出生（就是LocalDateTime所表达的），但如果我们根据时间线（如格林威治时间线）去仔细考察，则会发现在出生的人会比在英国出生的人稍微晚几个小时（这就是Instant所表达的概念，并且要将其转换为UTC格式的时间）。
————————————————
版权声明：本文为CSDN博主「Mandsence」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/fragrant_no1/article/details/83988042

        LocalDateTime localDateTime = LocalDateTime.now();
        
        LocalTime localTime = LocalTime.now();
        
        Month month = Month.valueOf(Month.JANUARY.name());
        
        int value = month.getValue();
        
        Month of = Month.of(12);
        
        Instant start = Instant.now();
        
        Calculator calculator = new ForLoopCalculator();
        
        calculator.sumUp(numbers);
        
        Instant end = Instant.now();
        
        System.out.println("耗时:"+ Duration.between(start,end).toMillis() + "ms");
