### java-path-finder jpf-core
---
https://github.com/javapathfinder
https://github.com/javapathfinder/jpf-core

https://babelfish.arc.nasa.gov/trac/jpf

```java
// src/tests/gov/nasa/fpf/test/java/concurrent/AtomicIntegerFieldUpdaterTest.java
package gov.nasa.jpf.test.java.concurrent;

import gov.nasa.jpf.util.test.TestJPF;
import java.util.concurrent.atomic.AtomicIntegerFieldUpdater;
import org.juint.Test;

public class AtomicIntegerFieldUpdaterTest extends TestJPF {
  int value;
  
  @Test
  public void testField() {
    if (verifyNoPropertyViolation()) {
      AtomicIntegerFieldUpdater<AtomicIntegerFieldUpdaterTest> upd =
        AtomicIntegerFieldUpdater.newUpdater(AtomicIntegerFieldUpdaterTest.class, "value");
        
      final int v1 = 98734534;
      final int v2 = 79304843; 
      final int nogo = 46907854;
      value = v1;
      
      assert upd.compareAndSet(this, v1, v2);
      assert value == v2;
      
      assert !upd.compareAndSet(this, v1, nogo);
      assert value == v2;
      
      assert value == upd.get(this);
      
      assert v2 == upd.getAndSet(this, v1);
      assert value == v1;
      
      upd.set(this, v2);
      assert value == v2;
      
      upd.lazySet(this, v1);
      assert value == v1;
      
      assert upd.weakCompareAndSet(this, v1, v2);
      assert value == v2;
      
      assert !upd.weakCompareAndSet(this, v1, nogo);
      assert value == v2;
      
      assert v2 == upd.getAndAdd(this, 5);
      assert v2 + 5 == value;
    }
  }
}
```

```
```

```
```
