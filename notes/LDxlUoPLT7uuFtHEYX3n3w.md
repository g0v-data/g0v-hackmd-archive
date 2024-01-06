---
title: "Visitor"
tags: hackpad
---

# Visitor

> [點此觀看原始內容](https://g0v.hackpad.tw/iOnq0iCkqcI)


```java
import java.util.;
public interface Checker {
 //訪問者check不同的對象會做不同的事情
 public void check(State s);
 //
 public void check(Transition t);
 //
 public void check(StateDiagram sd);
 //
}
public interface DiagramElement {
 //接受訪客訪問的介面
 public void accept(Checker c);
}
public class SyntaxCheck implements Checker{
 //SyntaxCheck實做checker
 public void check(State s) {
     //印出SytaxCheck State的結果
     System.out.println("SyntaxCheck");
 }
 public void check(Transition t) {
     System.out.println("SyntaxCheck");
 }
 public void check(StateDiagram sd) {
     System.out.println("SyntaxCheck");
 }
}
public class RelationCheck implements Checker{

 public void check(State s) {
     System.out.println("RelationCheck");
 }
 public void check(Transition t) {
     System.out.println("RelationCheck");
 }
 public void check(StateDiagram sd) {
     System.out.println("RelationCheck");
 }
}
public class State implements DiagramElement {

 @Override
 public void accept(Checker c) {
     //訪問這透過accept介面去check此物件
     c.check(this);
 }

}
public interface DiagramElement {
 //接受訪客訪問的介面
 public void accept(Checker c);
}
public class StateDiagram implements DiagramElement{
 private ArrayList<DiagramElement> element = new ArrayList<DiagramElement>();
 public void add(DiagramElement e){
     element.add(e);
 }
 @Override
 public void accept(Checker c) {
     //訪問這透過accept介面去check此物件
     c.check(this);

     Iterator itr = element.iterator();
     while(itr.hasNext()){
     //訪問者check StateDiagram底下的element
         ((DiagramElement)itr.next()).accept(c);
     }
 }

}



