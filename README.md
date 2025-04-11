## 📦 Spring XML 설정 템플릿

전통 Spring 환경에서 빠르게 적용할 수 있는 XML 설정 템플릿 모음입니다.  
공공 SI / 레거시 시스템 대응을 위해 실무에서 자주 사용되는 구성만 추려 정리했습니다.

---

### 🔧 구성 파일

| 파일명 | 설명 |
|--------|------|
| `applicationContext.xml` | Bean 등록, component-scan, DataSource, MyBatis, 트랜잭션 설정 포함 |
| `dispatcher-servlet.xml` | MVC 컨트롤러 설정, ViewResolver 설정 포함 |
| `tx-aop-context.xml` | 트랜잭션 Advice 및 AOP Pointcut 설정 포함 |

---

### 📌 예시 구조 (applicationContext.xml 일부)

```xml
<context:component-scan base-package="com.example" />

<bean id="dataSource" class="org.apache.commons.dbcp2.BasicDataSource">
    <property name="driverClassName" value="com.mysql.cj.jdbc.Driver" />
    <property name="url" value="jdbc:mysql://localhost:3306/example" />
    <property name="username" value="root" />
    <property name="password" value="password" />
</bean>

<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
    <property name="dataSource" ref="dataSource" />
</bean>
```

---

### 💡 사용 방법
	1.템플릿 복사 후 필요한 경로, DB 정보만 수정
	2.기존 프로젝트에 연동 (web.xml 또는 JavaConfig와 병행 가능)
	3.요한 설정 파일만 부분적으로 선택 사용 가능

 ---
 ### 📁 목적
•	공공기관/금융/레거시 시스템 대응<br>
•	트러블슈팅 시 XML 기반 로그 추적 및 수정 용이<br>
•	유지보수 및 신규 기능 추가 시 빠른 설정 재사용 가능<br>

 ---
 ### 📝 Tip
•	XML 설정은 구조가 반복되므로, 템플릿 형태로 만들어두고 복붙 후 경로만 수정하는 방식이 실무에서 일반적입니다.<br>
•	필요 시 이 템플릿을 spring-xml-templates GitHub 저장소로 관리하면 팀원과도 공유하기 좋습니다.<br>

---


 > 이 템플릿은 구조 설계 중심의 백엔드 개발을 지향하며,  
> 설정을 이해하고 직접 통제할 수 있는 개발자 성장을 돕기 위해 만들어졌습니다.

 
