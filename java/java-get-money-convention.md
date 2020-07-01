# Java Convention

```Java

int price1 = 123;
int price2 = 1234;
int price3 = 12345;
int price4 = 12345678;

DecimalFormat formatter = new DecimalFormat("###,###");

System.out.println(formatter.format(price1)); // 123
System.out.println(formatter.format(price2)); // 1,234
System.out.println(formatter.format(price3)); // 12,345
System.out.println(formatter.format(price4)); // 12,345,678
```
