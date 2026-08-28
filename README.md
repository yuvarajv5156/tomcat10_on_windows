# Apache Tomcat 10 Installation and Deployment on Windows

## 1. Install Java

Install JDK and verify Java:

```cmd
java -version
javac -version
```

Set `JAVA_HOME` to the JDK installation directory.

Example:

```text
C:\Program Files\Java\jdk-17
```

Verify:

```cmd
echo %JAVA_HOME%
```

---

## 2. Install Apache Tomcat 10

Download and extract Apache Tomcat 10.

Example location:

```text
C:\Apache\Tomcat
```

Important Tomcat folders:

* `bin` – Contains scripts to start and stop Tomcat.
* `conf` – Contains Tomcat configuration files.
* `lib` – Contains Java library/JAR files.
* `logs` – Contains Tomcat log files.
* `webapps` – Contains deployed web applications.
* `work` – Contains temporary/compiled application files.
* `temp` – Contains temporary files.

---

## 3. Start Tomcat

Open CMD and go to the Tomcat `bin` folder:

```cmd
cd C:\Apache\Tomcat\bin
```

Start Tomcat:

```cmd
startup.bat
```

Stop Tomcat:

```cmd
shutdown.bat
```

---

## 4. Access Tomcat

Open a browser:

```text
http://localhost:8080
```

If the port is changed to `9090`:

```text
http://localhost:9090
```

---

## 5. Configure Tomcat Manager

Edit:

```text
conf\tomcat-users.xml
```

Add a user with the required Manager roles.

Save the file and restart Tomcat.

Manager application:

```text
http://localhost:8080/manager/html
```

---

## 6. Deploy WAR File Directly

Copy the WAR file into:

```text
webapps
```

Example:

```text
webapps\book-seller.war
```

Tomcat automatically deploys the application.

Access it using:

```text
http://localhost:8080/book-seller
```

---

## 7. Deploy WAR File Using Tomcat Manager

Open:

```text
http://localhost:8080/manager/html
```

Go to **WAR file to deploy**.

1. Click **Choose File**.
2. Select `book-seller.war`.
3. Click **Deploy**.
4. The application will appear under **Applications**.

Access:

```text
http://localhost:8080/book-seller
```

---

## 8. Manage Applications

In Tomcat Manager:

* **Start** – Starts a stopped application.
* **Stop** – Stops an application temporarily.
* **Reload** – Reloads the application.
* **Undeploy** – Removes the application from Tomcat.

---

## 9. Change Tomcat Port

Open:

```text
conf\server.xml
```

Find:

```xml
<Connector port="8080"
```

Change it to:

```xml
<Connector port="9090"
```

Save the file.

Restart Tomcat:

```cmd
shutdown.bat
startup.bat
```

Now access Tomcat using:

```text
http://localhost:9090
```

Application:

```text
http://localhost:9090/book-seller
```

---

## 10. Verify Tomcat is Running

Open:

```text
http://localhost:9090
```

If the Tomcat page opens, Tomcat is running.

After executing:

```cmd
shutdown.bat
```

the Tomcat page should no longer open.

---

## 11. Important Tomcat Files

| File               | Purpose                                         |
| ------------------ | ----------------------------------------------- |
| `server.xml`       | Configures Tomcat server settings such as ports |
| `tomcat-users.xml` | Defines users and roles                         |
| `startup.bat`      | Starts Tomcat on Windows                        |
| `shutdown.bat`     | Stops Tomcat on Windows                         |
| `catalina.bat`     | Main Tomcat startup/control script              |

## Summary

```text
Java JDK
   ↓
Apache Tomcat 10
   ↓
Configure tomcat-users.xml
   ↓
Start Tomcat
   ↓
Open Tomcat Manager
   ↓
Deploy WAR file
   ↓
Access application
   ↓
Manage / Stop / Undeploy application
```

