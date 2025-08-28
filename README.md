# SPRING ADVANCED


# lv0
## 📌 원인 분석

````
2025-08-28T15:22:58.709+09:00 ERROR 19048 --- 
[main] o.s.b.web.embedded.tomcat.TomcatStarter  : Error starting Tomcat context. 
Exception: org.springframework.beans.factory.UnsatisfiedDependencyException. 
Message: Error creating bean with name 'filterConfig' defined in file [C:\baek\spring-advanced\build\classes\java\main\org\example\expert\config\FilterConfig.class]: 
Unsatisfied dependency expressed through constructor parameter 0: 
Error creating bean with name 'jwtUtil': Injection of autowired dependencies faile
````

FilterConfig 가 JwtUtil 빈을 생성자 주입받는 과정에서 실패함.

JwtUtil 내부를 확인해보니, @Value("${jwt.secret.key}") 로 설정값을 주입받고 있지만,

application.yml / application.properties 에 jwt.secret.key 설정이 없어서, secretKey 가 null → 초기화 과정에서 예외 발생 → 애플리케이션 실행 실패.

