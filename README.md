# solution-spring-rest-demo-helloworld
Mô tả
DemoRestController.java
Lớp DemoRestController định nghĩa một RESTful endpoint /test/hello để trả về chuỗi "Hello World!".

java
Copy code
@RestController
@RequestMapping("/test")
public class DemoRestController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello World!";
    }
}
StudentRestController.java
Lớp StudentRestController định nghĩa một RESTful endpoint /api/students để trả về danh sách sinh viên.

java
Copy code
@RestController
@RequestMapping("/api")
public class StudentRestController {

    @GetMapping("/students")
    public List<Student> getStudents() {
        List<Student> theStudents = new ArrayList<>();
        theStudents.add(new Student("poe", "nice"));
        theStudents.add(new Student("mary", "ten"));
        theStudents.add(new Student("sune", "fore"));

        return theStudents;
    }
}
MySpringMvcDispatcherServletInitializer.java
Lớp MySpringMvcDispatcherServletInitializer là một lớp cấu hình Servlet Dispatcher của Spring.

java
Copy code
public class MySpringMvcDispatcherServletInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {

    @Override
    protected Class<?>[] getRootConfigClasses() {
        return null;
    }

    @Override
    protected Class<?>[] getServletConfigClasses() {
        return new Class[]{DemoAppConfig.class};
    }

    @Override
    protected String[] getServletMappings() {
        return new String[]{"/"};
    }
}
Kết quả
Khi chạy ứng dụng và truy cập vào các URL sau:

http://localhost:8080/test/hello: Trang sẽ hiển thị chuỗi "Hello World!".
http://localhost:8080/api/students: Trang sẽ hiển thị danh sách sinh viên được trả về dưới dạng JSON.
