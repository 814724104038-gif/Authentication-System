# 🔐 JSP + Servlet + JDBC Authentication System

## 📋 **Project Overview**
A complete, modern authentication system built with **JSP (Frontend)**, **Servlet (Backend)**, and **JDBC (Database)** featuring attractive animations, responsive design, and secure user management.

## 🚀 **Technology Stack**
- **Frontend**: JSP, HTML5, CSS3, JavaScript
- **Backend**: Jakarta Servlet (Tomcat 10.1 compatible)
- **Database**: MySQL with JDBC
- **Security**: Session Management, Form Validation
- **Styling**: Modern CSS with Animations, Font Awesome Icons

## 📁 **Project Structure**
```
AuthenticationSystem/
├── src/
│   ├── com.auth.controller/
│   │   └── AuthServlet.java          # Main servlet for routing
│   ├── com.auth.dao/
│   │   └── UserDAO.java              # Database operations
│   ├── com.auth.model/
│   │   └── User.java                 # User model class
│   └── com.auth.util/
│       └── DatabaseConnection.java    # DB connection utility
├── WebContent/
    |----screenshots
│   ├── css/
│   │   └── style.css                 # Main stylesheet
│   ├── js/
│   │   └── animations.js             # UI animations
│   ├── login.jsp                     # Login page
│   ├── register.jsp                  # Registration page
│   ├── success.jsp                   # Welcome dashboard
│   ├── error.jsp                     # Error handling page
│   └── WEB-INF/
│       ├── web.xml                   # Deployment descriptor
│       └── lib/                      # JAR libraries
│           ├── mysql-connector-java.jar
│           └── jbcrypt.jar (optional)
```

## ⚙️ **Prerequisites**
1. **Java Development Kit (JDK)** 11 or higher
2. **Eclipse IDE** for Enterprise Java Developers
3. **Apache Tomcat** 10.1
4. **MySQL** Database Server
5. **MySQL Connector/J** 8.0+

## 🛠️ **Setup Instructions**

### **1. Database Setup**
```sql
CREATE DATABASE auth_system;
USE auth_system;

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Test data (optional)
INSERT INTO users (username, password, email) 
VALUES ('admin', 'admin123', 'admin@example.com');
```

### **2. Eclipse Project Setup**
1. **File → New → Dynamic Web Project**
2. Project Name: `AuthenticationSystem`
3. Target Runtime: **Apache Tomcat v10.1**
4. Configuration: **Default Configuration**
5. Check **Generate web.xml deployment descriptor**

### **3. Add Dependencies**
Copy these JARs to `WebContent/WEB-INF/lib/`:
- `mysql-connector-j-8.0.33.jar`
- `jbcrypt-0.4.jar` (optional for password hashing)

### **4. Configure Database Connection**
Edit `DatabaseConnection.java`:
```java
private static final String URL = "jdbc:mysql://localhost:3306/auth_system";
private static final String USERNAME = "root";      // Your MySQL username
private static final String PASSWORD = "password";  // Your MySQL password
```

## 🌟 **Features**

### **🎨 Modern UI/UX**
- Gradient backgrounds and glass-morphism effects
- Smooth animations and transitions
- Responsive design for all devices
- Interactive form validation
- Loading spinners and progress indicators

### **🔐 Security Features**
- Session management with timeout
- Form validation (client & server side)
- Password strength indicator
- Secure password handling
- Error handling and logging

### **📱 Pages**

#### **1. Login Page (`login.jsp`)**
- Clean login form with username/password
- Password visibility toggle
- Remember me functionality
- Social login placeholders
- Demo credentials section

#### **2. Registration Page (`register.jsp`)**
- Multi-step registration form
- Real-time password strength meter
- Terms & conditions agreement
- Email format validation
- Progress indicator

#### **3. Success Dashboard (`success.jsp`)**
- Personalized welcome message
- User profile display
- Session information
- Dashboard with quick actions
- Security status indicator

#### **4. Error Page (`error.jsp`)**
- User-friendly error messages
- Debug information (development only)
- Helpful troubleshooting tips
- Contact support option

### **⚙️ Backend Features**
- **Single Servlet** for all authentication operations
- **JDBC** for database connectivity
- **Proper routing** based on request parameters
- **Session tracking** and management
- **Input validation** and sanitization

## 🚀 **Deployment**

### **1. Build Project**
1. Right-click project → **Export → WAR file**
2. Save as `AuthenticationSystem.war`

### **2. Deploy to Tomcat**
```bash
# Copy WAR file to Tomcat webapps
cp AuthenticationSystem.war /path/to/tomcat/webapps/

# Start Tomcat
/path/to/tomcat/bin/startup.sh
# or on Windows
/path/to/tomcat/bin/startup.bat
```

### **3. Access Application**
```
http://localhost:8080/AuthenticationSystem/
http://localhost:8080/AuthenticationSystem/login.jsp
http://localhost:8080/AuthenticationSystem/register.jsp
```

## 🧪 **Testing**

### **Test Users**
1. **Default Admin**
   - Username: `admin`
   - Password: `admin123`

2. **Registration Flow**
   - Fill registration form
   - Verify email format
   - Test password matching
   - Complete registration
   - Login with new credentials

### **Test Cases**
1. ✅ Valid login with correct credentials
2. ❌ Invalid login with wrong password
3. ✅ Successful registration
4. ❌ Registration with existing username
5. ❌ Registration with mismatched passwords
6. ✅ Session persistence
7. ✅ Logout functionality

## 🔧 **Troubleshooting**

### **Common Issues**

#### **1. Database Connection Error**
```java
// Check MySQL service is running
sudo systemctl status mysql

// Verify credentials in DatabaseConnection.java
// Test connection with:
Connection conn = DriverManager.getConnection(URL, USERNAME, PASSWORD);
```

#### **2. 404 Error on Servlet**
```xml
<!-- Check web.xml configuration -->
<servlet>
    <servlet-name>AuthServlet</servlet-name>
    <servlet-class>com.auth.controller.AuthServlet</servlet-class>
</servlet>
<servlet-mapping>
    <servlet-name>AuthServlet</servlet-name>
    <url-pattern>/auth</url-pattern>
</servlet-mapping>
```

#### **3. ClassNotFoundException**
- Verify JAR files in `WEB-INF/lib/`
- Check Build Path in Eclipse
- Clean and rebuild project

#### **4. Tomcat 10.1 Compatibility**
- Use **Jakarta** packages, not **javax**
- Ensure Servlet API 5.0+
- Check deployment descriptor version

### **Debug Mode**
Enable debug logging in `AuthServlet.java`:
```java
System.out.println("DEBUG: Processing " + request.getMethod() + " request");
System.out.println("DEBUG: Action: " + action);
System.out.println("DEBUG: Username: " + username);
```

## 📝 **Configuration Files**

### **web.xml**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="https://jakarta.ee/xml/ns/jakartaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="https://jakarta.ee/xml/ns/jakartaee
         https://jakarta.ee/xml/ns/jakartaee/web-app_5_0.xsd"
         version="5.0">
    
    <display-name>Authentication System</display-name>
    
    <welcome-file-list>
        <welcome-file>login.jsp</welcome-file>
    </welcome-file-list>
    
    <session-config>
        <session-timeout>30</session-timeout>
    </session-config>
    
    <error-page>
        <error-code>404</error-code>
        <location>/error.jsp</location>
    </error-page>
    
    <error-page>
        <error-code>500</error-code>
        <location>/error.jsp</location>
    </error-page>
</web-app>
```

## 🎯 **Learning Objectives**

### **Concepts Covered**
1. **MVC Architecture** with JSP and Servlet
2. **Database Connectivity** with JDBC
3. **Session Management** in web applications
4. **Form Handling** and validation
5. **Error Handling** and user feedback
6. **Security Best Practices**
7. **Responsive Web Design**

### **Skills Developed**
- ✅ Building complete web applications
- ✅ Implementing authentication systems
- ✅ Database design and operations
- ✅ Frontend-backend integration
- ✅ Debugging web applications
- ✅ Deployment and testing

## 📚 **Extensions & Improvements**

### **For Learning**
1. Add **email verification** system
2. Implement **password reset** functionality
3. Add **remember me** with cookies
4. Implement **CAPTCHA** for security
5. Add **user profile** management

### **For Production**
1. Implement **password hashing** with BCrypt
2. Add **HTTPS/SSL** support
3. Implement **rate limiting**
4. Add **logging** and monitoring
5. Database connection pooling

### **Advanced Features**
1. **Two-factor authentication**
2. **Social login** integration
3. **Role-based access control**
4. **Activity logging**
5. **API integration**

## 🤝 **Contributing**

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 **License**

This project is for educational purposes. Feel free to use and modify for learning.

## 🆘 **Support**

For issues or questions:
1. Check the **Troubleshooting** section
2. Review the code comments
3. Test with provided demo credentials
4. Enable debug logging



