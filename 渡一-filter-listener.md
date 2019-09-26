### FIlter

<hr>



#### 1��FIlter����������

��1��Tomcat�ṩ��һ�����������Servlet����

��2����һ�������Servlet

��3�����˵ı��ʣ�ʹ�ó���



##### 1��filter����ʹ��

> HttpFilter��Tomcat9�ṩ�ģ�9֮ǰ�汾ֱ��ʵ��Filter�ӿ�
>
> ��Ҫ������doFilter��init��destroy
>
> �쳣��ServletException��IOException
>
> ���ã�
>
> ```xml
> <filter>
> 	<filter-name>loginFilter</filter-name>
>     <filter-class>filter.LoginFilter</filter-class>
> </filter>
> <filter-mapping>
> 	<filter-name>loginFilter</filter-name>
>     <url-pattern>/login</url-pattern>
> </filter-mapping>
> ```

java���룺

```java
public class LoginFilter extends HttpFilter {
    public void doFilter(request,response,chain){
        System.out.println("catch the request");
        chain.doFilter(request,response);
    }
}
```



Ӧ�ó�����

ÿһ��Servlet�Ǿ�����ĳһ����

һ��Filter���Ժܶ����󾭹��������ھ���Servlet֮ǰ��֮�����ִ��һЩ��ͬ�Ĳ�����

����ʹ�ã��û���֤���������ַ�������



������ƣ�

��1��filter������һ��������

��2��filter������һ���������صķ�ʽ������ͨ������load-on-startup�������޸ģ���Ϊ������Servletһ��Ĭ����ʱ����

��3��������������󶼴�����ͬ���󣬸��������ļ�˳��ִ�У�������ʵ��Դִ��֮ǰ��֮��������



##### 2��������ģʽ

����������͵����󶼻ᾭ��Filter

�ӷ�����ת��forward��Ĭ���ǲ�����filter��`request.getRequestDispatcher("index.jsp").forward(request,response)`



�ӷ������ض��������ᱻFilter����

ԭ��

```xml
<filter>
	<filter-name>loginFilter</filter-name>
    <filter-class>filter.LoginFilter</filter-class>
</filter>
<filter-mapping>
	<filter-name>loginFilter</filter-name>
    <url-pattern>/*</url-pattern>
    <!--��������ã�Ĭ��ֻ����request��ת��������-->
    <dispatcher>REQUEST</dispatcher>
    <!--���������forward��ֻ����forward����������-->
    <!--��Ҫ���صĻ���������Ҫ���ã�����forward�Ḳ��Ĭ�ϵ�request-->
    <dispatcher>FORWARD</dispatcher>
</filter-mapping>
```



filter����ʹ�����������ģʽ��Chain Of Responsibility Pattern��



���������ģʽ

```java
//�������filter��ִ��
public class ApplicationFilterChain implements FilterChain {
    //�洢����Filter������
    private ArrayList<HttpFilter> filterList = new ArrayList<>();
    private int size = 0;

    //���filter
    public void addFilter (HttpFilter filter){
        filterList.add(filter);
    }

    //�����м�����Ԫ�ص�doFilter����ִ��
    public void doFilter () {
        if(size < filterList.size()){
           HttpFilter filter = filterList.get(size++);
           filter.doFilter(this);
        }else{
            System.out.println("���е�������ִ����ϣ���������controller�ķ���ִ��");
        }
    }
	
    //����������
    public static void main(String[] args) {
        FilterChain filterChain = new ApplicationFilterChain();
        for(int i = 1; i < 10; i++){
            filterChain.addFilter(new DoFilter(i));
        }
        filterChain.doFilter();
    }
}

//����ɻ�Ĺ�����
public class DoFilter extends HttpFilter {
    private int index;

    public DoFilter (int index){
        this.index = index;
    }

    @Override
    public void doFilter(FilterChain chain) {
        System.out.println(index + "��Filter����ִ��");
        chain.doFilter();
    }
}

//�������ƶ�����
public abstract class HttpFilter {
    public abstract void doFilter(FilterChain chain);
}

//�ƶ�������ʵ����ʽ�ɻ�Ĺ���
public interface FilterChain {
    void doFilter();
    void addFilter(HttpFilter filter);
}
```



����Tomcat��Filterԭ��

> 1���������������Tomcat��������
>
> 2��Tomcat����web.xml�����ļ��������е�Filter��ͨ�������ö���
>
> 3��ͨ����̬�齫����Ž������ͨ��������ģʽ�����÷���
>
> 4������Filter����ʱ����������ϣ����а����������Filter����ִ��
>
> 5������doFilter����ִ����󣬷��к󽻸������Servletʵ����ִ��
>
> 6���ݹ��������Filter�ķ��к����

��Filter̫���ʱ���ռ��ջ�ڴ���࣬����Springʹ��AOP��Ч�ʸ���







#### 2��������

Listener��������

��1�����������Ĳ���������

��2������������ֵ���޸ġ�ɾ��

��3�������������request��session��application

��4��������������`ServletRequestListener`,`HttpSessionListener`,`ServeltContextListener`

��5���������Լ�������

������ֵ��ȡֵ�����ĵķ���

`ServletRequestAttibuteListener`��`HttpSessionAttributeListener`��`ServletContextAttributeListener`



�����������ļ�

```xml
<listener>
	<listener-class>listener.Demo</listener-class>
</listener>
```



����

���������������٣���ֵȡֵʱ����

