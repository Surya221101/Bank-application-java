# Bank-application-java
//I have created a bank application for withdrawal of money in java using synchronized threading
package multithreading;

//import java.util.Scanner;

class BankDemo extends Thread{
	//int bal;
  void get(int bal,int amt) {
	 /* Scanner sc=new Scanner(System.in);
	  System.out.println("Enter balance in your account");
	  bal=sc.nextInt();*/
	 	synchronized (this) {
		  if(bal<amt) {
			  System.out.println("Insufficient balance");
		  }
		  else
		  {
			  bal=bal-amt;
			  if(bal<5000) {
				  System.out.println("Balance low than minimum balance"+Thread.currentThread()+"Must be 5000");
			  }
			  else {
				  System.out.println("Transaction successful"+"by"+Thread.currentThread()+" "+"Balance="+bal);
			  }
		  }
		}
  }
  public void run() {
	  for(int i=0;i<5;i++) {
		  try {
			  Thread.sleep(2500);
			  get(50000,10000);
		  }
		  catch(InterruptedException e) {
			  System.out.println(e);
		  }
	  }
  }
}
public class Demo5 {

	public static void main(String[] args) {
		BankDemo b1=new BankDemo();
		b1.setName("Ram");
		b1.start();
		BankDemo b2=new BankDemo();
		b2.setName("Shyam");
		b2.start();
	}

}
