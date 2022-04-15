``` 
숫자를 정수로 하거나 정수를 숫자로 하거나 아무튼 그런것들
```

System.out.println(Integer.parseInt("-123")); // 문자열 “-123”을 정수로 변환하여 출력

System.out.println(Integer.parseInt("10", 16)); // 16진수로 표현된 문자열 “10”을 정수로 변환하여 출력

System.out.println(Integer.toBinaryString(28)); // 28의 2진수 표현을 나타내는 문자열 출력

System.out.println(Integer.bitCount(28)); // 28의 2진수에서 1의 개수출력

System.out.println(Integer.toHexString(28)); // 28의 16진수 표현을 나타내는 문자열 출력

System.out.println(i.doubleValue()); // i값(=10)을 double로 변환하여 출력

System.out.println(d.toString()); // d값(=3.1234566)을 문자열로 변환하여 출력

System.out.println(Double.parseDouble("44.13e-6")); // 문자열 “44.13e-16"을 double로 변환하여 출력