# ExampleAddOn for MCEngine Artificial Intelligence

This is an example add-on for the `MCEngineArtificialIntelligence` plugin. It demonstrates how to implement and register a custom AI module using the provided `IMCEngineArtificialIntelligenceAddOn` interface.

## 📦 Dependency Setup

Add the `mcengine-artificialintelligence-api` to your project:

### ➤ Maven
```xml
<dependency>
  <groupId>io.github.mcengine</groupId>
  <artifactId>mcengine-artificialintelligence-api</artifactId>
  <version>{version}</version>
</dependency>
```

### ➤ Gradle (long form)
```groovy
dependencies {
    implementation group: 'io.github.mcengine', name: 'mcengine-artificialintelligence-api', version: '{version}'
}
```

### ➤ Gradle (short form)
```groovy
implementation 'io.github.mcengine:mcengine-artificialintelligence-api:{version}'
```

---

## 🧩 Implementing an AddOn

Your add-on class must implement the following interface:

```java
public interface IMCEngineArtificialIntelligenceAddOn {
    void onLoad(Plugin plugin);
}
```

### ✅ Example Implementation

```java
package io.github.mcengine.addon.example;

import io.github.mcengine.api.artificialintelligence.addon.IMCEngineArtificialIntelligenceAddOn;
import io.github.mcengine.api.artificialintelligence.addon.MCEngineArtificialIntelligenceAddOnLogger;
import org.bukkit.plugin.Plugin;

public class ExampleAddOn implements IMCEngineArtificialIntelligenceAddOn {

    private MCEngineArtificialIntelligenceAddOnLogger logger;

    @Override
    public void onLoad(Plugin plugin) {
        logger = new MCEngineArtificialIntelligenceAddOnLogger(plugin, "ExampleAddOn");
        logger.info("ExampleAddOn is loading...");
        
        // Add your AI behavior, listeners, or logic here
        
        logger.info("ExampleAddOn has loaded successfully.");
    }
}
```

---

## 📁 Packaging

Make sure your JAR file includes the `ExampleAddOn` class and any dependencies required for your logic. Place the final JAR into the `plugins/MCEngineArtificialIntelligence/addons/` directory.

---

## 🔄 Dynamic Loading

The core MCEngine plugin will detect and load this add-on automatically if it implements the interface `IMCEngineArtificialIntelligenceAddOn`.

---
