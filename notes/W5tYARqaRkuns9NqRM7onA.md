---
title: "Composite"
tags: hackpad
---

# Composite

> [點此觀看原始內容](https://g0v.hackpad.tw/GR01FzDqs4n)


```java
 import java.awt.Graphics;
 import java.awt.Point;
 import java.util.;

 public abstract class DiagramElement {
 String name;
 Point loc;
 public DiagramElement(){}
 public abstract void draw(Graphics g);
 public abstract boolean intersect(Point p);
 public void add(DiagramElement e){}
 public DiagramElement getElement(int de){
     return null;
 }
 public void remove(DiagramElement e){}
}
public class State extends DiagramElement{
 int width;
 int height;
 public State(){}

 @Override
 public void draw(Graphics g) {
     System.out.println("Draw state"); //To change body of generated methods, choose Tools | Templates.
 }

 @Override
 public boolean intersect(Point p) {
     throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
 }
 }
public class StateDiagram extends DiagramElement{
 private ArrayList<DiagramElement> des = new ArrayList<DiagramElement>();

 public StateDiagram(){}

 public void add(DiagramElement e){
     des.add(e);
 }
 public DiagramElement getElement(int diagramElementIndex){
     System.out.println("----- get element into StateDiagram1 ----- ");
     return des.get(diagramElementIndex);
     //用index取出任意在State diagram底下的element
 }

 @Override
 public void draw(Graphics g) {
     Iterator<DiagramElement> iterator = des.iterator();
     while(iterator.hasNext()){
         iterator.next().draw(g);
     }
 }

 @Override
 public boolean intersect(Point p) {
. return true;
 }
 public ArrayList<DiagramElement> getChild(){
     return this.des;
 }
 public void remove(DiagramElement e){
     des.remove(e);
 }
}
public class Transition extends DiagramElement{
 Point dest;
 public Transition(){}
 @Override
 public void draw(Graphics g) {
     System.out.println("Draw transition"); //To change body of generated methods, choose Tools | Templates.
 }

 @Override
 public boolean intersect(Point p) {
     throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
 }
}

