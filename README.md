# Springboot Basic

> Spring Security

## 1. WebSecurityConfig.java

> WebSecurityConfig 这个类被 @EnableWebSecurity 注解。作用如下：

- 开启SpringSecurity
- 集成到当前 Spring MVC

> 继承自 WebSecurityConfigurerAdapter ，overrides a couple of its methods to set some specifics of the web security configuration.

- 重写了部分代码，目的是设定一些定制的 web security 配置

> The configure(HttpSecurity) method defines which URL paths should be secured and which should not. Specifically, the / and /home paths are configured to not require any authentication. All other paths must be authenticated.

- configure(HttpSecurity) 函数 定义了哪些 URL PATH 被保护，哪些不被保护。
- 从定制的代码来看： / 和 /home 是不需要任何的验证的
- 其他的 PATH 是一定需要验证的

```java
    protected void configure(HttpSecurity http)throws Exception{
        http
        .authorizeRequests()
        .antMatchers("/","/home").permitAll()
        .anyRequest().authenticated()
        .and()
        .formLogin()
        .loginPage("/login")
        .permitAll()
        .and()
        .logout()
        .permitAll();
        }
```



