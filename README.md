### cogcomp-nlp
---
https://github.com/CogComp/cogcomp-nlp

```java
// core-utilities/src/test/java/edu/illinois/cs/cogcomp/core/serch/SerchTest.java

public class SearchTest {
  IStateManager<Pair<Integer, Integer>> stateManager =
    new IStateManager<Pair<Integer, Integer>>() {
      public boolean goalTest(Pair<Integer, Integer> data) {
        return (data.getFirst() + data.getSecond()) >= 4;
      }
      
      public List<Pair<Integer, Integer>> nextStates(Pair<Integer, Integer> currentState) {
        List<Pair<Integer, Integer>> list = new ArrayList<>();
        
        list.add(new Pair<>(currentState.getFirst() + 1, currentState.getSecond()));
        list.add(new Pair<>(currentState.getFirst(), currentState.getSecond() + 1));
        return list;
      }
    };
    
  public Integer score(Pair<Integer, Integer> element) {
    return Math.max(elemet.getFirst(), element.getSecond());
  }
  
  @Test
  public final void testDepthFirstSearch() {
    DepthFirstSearch<Pair<Integer, Integer>> dfs = new DepthFirstSearch<>();
    
    Pair<Integer, Integer> result = (dfs.search(new Pair<>(0, 0), stateManager));
    
    assertEquals(result, new Pair<>(0, 4));
  }
  
  @Test
  public final void testBreadthFirstSearch() {
    GraphSearch<Pair<Integer, Integer>> dfs = new DepthFirstSearch<>();
    
    Pair<> result = (dfs.search(new Pair<>(0, 0), stateManager));
    
    assertEquals(result, new Pair<>(0, 4));
  }
  
  @Test
  public final void testUniformCostSearch() {
    GraphSearch<Pair<Integer, Integer>> dfs =
      new UniformCostSearch<>(new Comparator<Pair<Integer, Integer>>() {
        public int compare(Pair<Integer, Integer> o1, Pair<Integer, Integer> o2) {
          return -score(o1).compareTo(score(o2));
        }
      });
      
    Pair<Integer, Integer> result = (dfs.search(new Pair<>(0, 0), stateManager));
    assertEquals(result, new Pair<>(4, 0));
  }
  
  @Test
  public final void testBeamSearch() {
    GraphSearch<Pair<Integer, Integer>> dfs = 
      new BeamSearch<>(4, new Comparator<Pair<Integer, Integer>>() {
        public int compare(Pair<Integer, Integer>o1, Pair<Integer, Integer> o2) {
          return -score(o1).compareTo(score(o2));
        } 
      });
    
    Pair<Integer, Integer> result = (dfs.search(new Pair<>(0, 0), stateManager));
    
    assertEquals(result, new Pair<>(4, 0));
  }
}
```

```
```

```
```


