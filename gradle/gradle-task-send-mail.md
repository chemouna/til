
## Gradle task to send an email

A gradle task to send an email automatically :

```gradle

configurations { antClasspath }
dependencies {
    antClasspath 'ant:ant-javamail:1.6.5'
    antClasspath 'javax.activation:activation:1.1.1'
    antClasspath 'javax.mail:mail:1.4.7'
}
ClassLoader antClassLoader = org.apache.tools.ant.Project.class.classLoader
configurations.antClasspath.each { File jar ->
    println "Adding to ant classpath : " + jar.absolutePath
    antClassLoader.addURL(jar.toURI().toURL())
}

def sendMailTask = project.task("sendMail") << {
    def mailParams = [
            mailhost       : "smtp.gmail.com",
            mailport       : "465",
            subject        : "Email Recieved",
            messagemimetype: "text/plain",
            user           : "myemail@gmail.com",
            password       : "mypassword",
            enableStartTLS : "true",
            ssl            : "true"
    ]
    println 'Mail Sending Start..'
    ant.mail(mailParams) {
        from(address: 'from_mail@gmail.com')
        to(address: 'tomail@gmail.com')
        message("Here I go through Gradle!!")
    }
}

```
