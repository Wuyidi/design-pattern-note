## Singleton Pattern (2)

### Load Balancer

![LoadBalancer](./Images/LoadBalancer.svg)

LoadBalancer.java

```java
import java.util.*;
enum LoadBalancer {
  INSTANCE;
  
  private List serverList;
  
  private LoadBalancer() {
    serverList = new ArrayList();
  }
  
  public void addServer(String server) {
    serverList.add(server);
  }
  
  public void removeServer(String server) {
    serverList.remove(server);
  }
  
  public String getServer() {
    Random random = new Random();
    int i = random.nextInt(serverList.size());
    return (String)serverList.get(i);
  }
}
```

Client.java

```java
class Client {
  public static void main(String args[]) {
    LoadBalancer balancer1,balancer2,balancer3,balancer4;
    balancer1 = LoadBalancer.INSTANCE;  
    balancer2 = LoadBalancer.INSTANCE;  
    balancer3 = LoadBalancer.INSTANCE;
    balancer4 = LoadBalancer.INSTANCE;
    if (balancer1 == balancer2 && balancer2 == balancer3 && balancer3 == balancer4) {
      System.out.println("There is only one load balancer")
    }
    
    balancer1.addServer("Server 1");
    balancer1.addServer("Server 2");
    balancer1.addServer("Server 3");
    balancer1.addServer("Server 4");
    
    for (int i = 0; i < 10; i++) {
      String server = balancer1.getServer();
      System.out.println("Send request to " + server);
    }
  }
}
```



