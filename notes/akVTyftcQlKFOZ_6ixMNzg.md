![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d0b7842f8f35d1ec538e2450b7d5a76f.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_55821c1511854ac62cb79a775e47aa3d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4bbfb14b9a998abc87913b4de57e1e65.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_67909c1cf950a9fa1b409de33d079416.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a690edf448573cfc7f308a1a923a2b0f.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66c5f9c5a05a6454d02b2e60ff3ae743.png)

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