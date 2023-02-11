### aspect 笔记

@Pointcut 语法:

```java

execution(public **(..))

@annotation(注解的全类名)

// 任意set开头的方法
execution(* set*(..))

// AccountService 接口的任意方法执行
execution(* com.xyz.service.AccountService.*(..))

// service包和其所有子包的任意方法执行
execution(* com.xyz.service..*.*(..))

// service包里任意类的方法执行
within(com.xyz.service.*)

```

@Before 前置通知

@After 后置通知

@Around 环绕通知

@AfterReturning 成功执行方法之后调用通知

@AfterThrowing 方法抛出异常之后调用通知

执行顺序:

正常情况: around -> before -> invoke -> after returning -> after -> around

异常情况: around -> before -> invoke -> after throwing -> after

```java
    @Pointcut("@annotation(org.springframework.web.bind.annotation.GetMapping)")
    public void pointcut() {

    }

    @Before("pointcut()")
    public void before() {
        System.out.println("before advice");
    }

    @Around("pointcut()")
    public void around(ProceedingJoinPoint joinPoint) throws Throwable {
        System.out.println("before around");
        joinPoint.proceed();
        System.out.println("after around");
    }

    @After("pointcut()")
    public void after() {
        System.out.println("after advice");
    }

    @AfterReturning("pointcut()")
    public void afterReturning() {
        System.out.println("after returning");
    }

    @AfterThrowing("pointcut()")
    public void afterThrowing(){
        System.out.println("after throwing");
    }

```
