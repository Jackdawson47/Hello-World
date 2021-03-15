# Hello-World
Just getting to know GitHub
now I am editing on the new readme. this is my code:
package Objects_Class;
import java.io.PipedWriter;
import java.util.ArrayList;
import java.io.Console;
import java.util.Scanner;

import java.util.*;

interface Person {

    public abstract String getDetails();
}
class Professor implements Person {
    protected int initialSalary;

    public Professor(int initialSalary) {
        this.initialSalary = initialSalary;
    }
    public String getDetails () {
        return "initial salary is " +initialSalary;
    }
}

class Student implements Person {

    private int year;
    public static final int annualFees = 10000;
    protected BankAccount bankAccount;

    public Student (int year, BankAccount bankAccount) {
        this.year= year;
        this.bankAccount = bankAccount;
    }
    public String getDetails() {
        return  "bank account number is " +bankAccount.accountNumber;

    }

    public int getYear() {
        return year;
    }

    public int computeFees( ) {
        return Student.annualFees * year ;
    }
}



class ResearchStudent extends Student {
   protected String researchArea;

    public ResearchStudent (int year, BankAccount bankAccount, String researchArea) {
        super (year, bankAccount);
        this.researchArea = researchArea;
    }
    public int computeFees(int multiplier) {
        return Student.annualFees  * multiplier ;
    }
}

class Phdstudent extends ResearchStudent {
    private int numOfTeachingYears;
    private String thesisTitle;
    private int scholarship;

    public Phdstudent(int year, BankAccount bankAccount,
                      String researchArea,  String thesisTitle, int numOfTeachingYears, int scholarship) {
        super(year,bankAccount,researchArea);
        this.thesisTitle = thesisTitle;
        this.numOfTeachingYears = numOfTeachingYears;
        this.scholarship = scholarship;
    }

    public String getDetails() {
        return super.getDetails() +" " +"research area is " +researchArea +" thesis title is " +thesisTitle
                +" his scholarship amount is " +scholarship;

    }
    public int computeFees() {
        return Student.annualFees * numOfTeachingYears ;
    }



}

class BankAccount {
    protected int accountNumber;
    protected int balance;

    public BankAccount(int accountNumber, int balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
    }
}

public class InformationManagementSystem {
    public static void main(String[] args) {
        BankAccount account1 = new BankAccount(133311, 80000);
        BankAccount account2 = new BankAccount(12121, 88);
        Student s1 = new Student( 2, account1);
//        System.out.println(s1.getDetails());

        Phdstudent s2 = new Phdstudent( 3, account1,
                "Computer science", "mastering blockchain", 5, 30000);
//        System.out.println(s2.getDetails());

        Professor p1 = new Professor( 50000);
//        System.out.println(p1.getDetails());

        LinkedList array = new LinkedList();
        array.add(p1);
        array.add(s2);
        array.add(s1);
        array.add(new Phdstudent(3, account2, "Kanjira", "Mastering Music", 4, 33));
        printDetails(array);
       array.set(0, s1);
    }
    public static void printDetails (LinkedList array) {
        for (Object o : array) {
            Person p = (Person) o;
            System.out.println(p.getDetails());
        }
    }




}
