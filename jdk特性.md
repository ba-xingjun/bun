# time

nstant 类代表的是某个时间（有点像 java.util.Date），准确的说是：”是不带时区的即时时间点“，它是精确到纳秒的（而不是象旧版本的Date精确到毫秒）。如果使用纳秒去表示一个时间则原来使用一位Long类型是不够的，需要占用更多一点的存储空间，实际上其内部是由两个Long字段组成，第一个部分保存的是自标准Java计算时代（就是1970年1月1日开始）到现在的秒数，第二部分保存的是纳秒数（永远不会超过999,999,999）。

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
