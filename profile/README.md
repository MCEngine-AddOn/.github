# ExampleAddOn for MCEngine Projects

This is an example add-on for the `MCEngine{project name}` plugin. It demonstrates how to implement and register a custom AI module using the provided `IMCEngine{project name}AddOn` interface.

## 📦 Dependency Setup

To access GitHub Packages, you need to create two environments for authentication in your GitHub project and generate a personal access token with the appropriate permissions.

```env
GIT_USER_NAME={your name}
GIT_USER_TOKEN={your token}
```

**Note:**
- Your token must have the `read:packages` permission enabled.
- Public GitHub packages can be accessed using a token, even if the user is not part of the organization or repository.

Add the `mcengine-{project name}-api` to your project:

### ➤ Maven Repository
```xml
<repositories>
    <repository>
        <id>github</id>
        <url>https://maven.pkg.github.com/MCEngine/{project name}</url>
        <releases>
            <enabled>true</enabled>
        </releases>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
    </repository>
</repositories>

<servers>
    <server>
        <id>github</id>
        <username>${env.GIT_USER_NAME}</username>
        <password>${env.GIT_USER_TOKEN}</password>
    </server>
</servers>
```

### ➤ Maven
```xml
<dependency>
  <groupId>io.github.mcengine</groupId>
  <artifactId>mcengine-{project name}-api</artifactId>
  <version>{version}</version>
</dependency>
```

### ➤ Gradle Repository
```groovy
repositories {
    maven {
        url = uri('https://maven.pkg.github.com/MCEngine/{project name}')
        credentials {
            username = System.getenv('GIT_USER_NAME') ?: 'null'
            password = System.getenv('GIT_USER_TOKEN') ?: 'null'
        }
    }
}
```

### ➤ Gradle (long form)
```groovy
dependencies {
    implementation group: 'io.github.mcengine', name: 'mcengine-{project name}-api', version: '{version}'
}
```

### ➤ Gradle (short form)
```groovy
implementation 'io.github.mcengine:mcengine-{project name}-api:{version}'
```

---

## 🧩 Implementing an AddOn

Your add-on class must implement the following interface:

```java
public interface IMCEngine{project name}AddOn {
    void onLoad(Plugin plugin);
}
```

### ✅ Example Implementation

```java
package io.github.mcengine.addon.example;

import io.github.mcengine.api.{project name}.addon.IMCEngine{project name}AddOn;
import io.github.mcengine.api.{project name}.addon.MCEngine{project name}AddOnLogger;
import org.bukkit.plugin.Plugin;

public class ExampleAddOn implements IMCEngine{project name}AddOn {

    private MCEngine{project name}AddOnLogger logger;

    @Override
    public void onLoad(Plugin plugin) {
        logger = new MCEngine{project name}AddOnLogger(plugin, "ExampleAddOn");
        logger.info("ExampleAddOn is loading...");
        
        // Add your AI behavior, listeners, or logic here
        
        logger.info("ExampleAddOn has loaded successfully.");
    }
}
```

---

## 📁 Packaging

Make sure your JAR file includes the `ExampleAddOn` class and any dependencies required for your logic. Place the final JAR into the `plugins/MCEngine{project name}/addons/` directory.

---

## 🔄 Dynamic Loading

The core MCEngine plugin will detect and load this add-on automatically if it implements the interface `IMCEngine{project name}AddOn`.

---

<div align="center">

<h3><b>📦 Available Project</b></h3>

<a href="https://github.com/MCEngine-AddOn/example"><code>Example</code></a>

<h3><b>📁 Projects</b></h3>

<table>
  <tr>
    <td><a href="https://github.com/MCEngine/artificialintelligence"><code>artificialintelligence</code></a></td>
  </tr>
</table>

</div>

---
