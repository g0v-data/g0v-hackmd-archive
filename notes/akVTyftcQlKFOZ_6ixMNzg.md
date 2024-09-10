
處理iterator
```Java
  Iterator it=mylist.iterator();
      while(it.hasNext()){
         //System.out.println("@@@");
         Object element =  it.next();
         //System.out.println(element);
         if( !(element instanceof String)){//Hints: use instanceof operator
            it.remove(); 
              //System.out.println("remove@@@");
            }
          
         if((element instanceof String) && "###".equals(element))//Hints: use instanceof operator
			break;
		}
```


處理interface
```Java
interface AdvancedArithmetic{
  int divisor_sum(int n);
}

class MyCalculator implements AdvancedArithmetic
{


    
     String getName(){
        return "MyCalculator";
    }


    public void ImplementedInterfaceNames() {
        // TODO Auto-generated method stub
        
    }


	@Override
	public int divisor_sum(int n) {
		// TODO Auto-generated method stub
		return 0;
	}
}
```
處理Comparator
```Java
class Checker implements Comparator<Object>{

    @Override
    public int compare(Object o1, Object o2) {
        Player a = (Player) o1;
        Player b = (Player) o2;
        // TODO Auto-generated method stub
        int as = a.score;
        int bs = b.score;
        String ass = a.name;
        String bss = b.name;
        if(as>bs){
            return -1;
        } else if (as < bs) {
            return 1;
        } else {
             return (ass).compareTo(bss); 
        }
    }
     
}


  Collections.sort(tmp, new Comparator<Contest>
	   
```


   Collections.sort(list);