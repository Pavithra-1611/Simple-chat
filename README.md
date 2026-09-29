# Simple Chatting System (JSP + Servlet + AJAX + JDBC + MySQL)

Two pages only: `login.jsp` (login) and `chat.jsp` (send / view messages).
Messages are stored in MySQL and sent/received with AJAX (no page refresh).
The chat table shows **Sender | Receiver | Message | Time**.

## Requirements
- JDK 8+
- Apache Tomcat 9.x (uses `javax.servlet`; for Tomcat 10+ change `javax.servlet` to `jakarta.servlet` in imports/pom)
- Maven 3.6+ (or add the MySQL connector JAR manually, see below)

## Database
Configured in `src/main/java/com/chat/util/DBConnection.java`
(host db01.dbhost.dev, port 5051, db db_454ntqrwm).
Tables `users` and `messages` are created automatically at startup
(`DBInitListener`). The same SQL is in `sql/schema.sql`.

## Build & Run
### Option A - Maven
    mvn clean package
Copy `target/SimpleChat.war` into Tomcat's `webapps/` folder and start Tomcat.
Open: http://localhost:8080/SimpleChat/

### Option B - Eclipse / IntelliJ (no Maven)
1. Import as a Dynamic Web Project (`src/main/java` = source, `src/main/webapp` = web content).
2. Download `mysql-connector-j-8.0.33.jar` into `src/main/webapp/WEB-INF/lib/`.
3. Add Tomcat 9 as the server and run.

## How to test
1. Open the app in two browsers (or normal + private window).
2. Log in as `alice` in one and `bob` in the other.
3. Pick the other user in "Chat with" (press the refresh button if the list is empty) and chat.
