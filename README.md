# cs61b-homework
key points: 

//1. how to construct the Date class & the Date object?

public class Date{
private int month;
private int day;
private int year;
/** Constructs a Date object corresponding to the given string.
   *  @param s should be a string of the form "month/day/year" where month must
   *  be one or two digits, day must be one or two digits, and year must be
   *  between 1 and 4 digits.  If s does not match these requirements or is not
   *  a valid date, the program halts with an error message.
public Date(int month, int day, int year){
if(!isValidDate(month,day,year))   // a method to check whether the Date is Valid
  System.exit(0);
  this.month=month;
  this.day=day;
  this.year=year;
  }
  public Date (String s){
  if (s.matches("\\d{1,2}\\/\\d{1,2}\\/\\d{1,4}")){
    string [] o = s.split("/");
    if(isValidDate(Integer.parseInt(o[0]),IntegerInt.parseInt(o[1]), Integer.parseInt(o[2])));
    {
    month=Integer.parseInt(o[0]);
    day=Integer.pareseInt(o[1]);
    year=Integer.parseInt(o[2]);
    }
  }else
       System.exit(0);}
       
//  2. how to check it is a leap year?

   public static boolean isLeapYear(int Year){
   if(year%4==0&&year%100!=0||year%400=0)
   return true;
   else return false;
   }
   
// 3. to check whether it is Valid Date :1.month first(when we test the validity of day in a month, we need to know the exact number     * of days in a month, so we need to construct a method/

   public static int daysInMonth(int month, int year){
   if(month<1||month>12)  
   System.exit(0);
   switch(month){
   case 2 : 
     if (isLeapYear(year）{
     return 29;
    } else
    return 28;
    case 4:
    case6:
    case9:
    case11:
      return 30;
      default:
      return 31;
      }
      }
public static boolean isValidDate (int month, int day, int year){
if (year < 1) {            // years prior to A.D.1 are NOT valid.
            return false;
            }else if (day < 1 || day > daysInMonth(month,year)){
            return false;
            }
            return true;
            }
//3. how to return a string representation of this date in the form month/day/year./

         public String toString() {
         String s=month + "/" + day + "/" +year;
         return s;
         }
//4. how to determine whether this date is before the Date d.
  public boolean isBefore(Date d){
   if( this.year> d.year){
   return false;
   }else if (this.year<d.year)
   return true;
   }else if (this.year==d.year)
   if (this.month>d.month)
   return false;
   if (this.month<d.month)
   return true;
   if (this.month==d.month)
     if (this.day< d.day){
     return true;}
     else return false;
 }
 //5. how to determine whether this date is after the Date d.
 
 public boolean isAfter(Date d) {
 if (this.year == d.year&& this.day==d.day&&this.month==d.month){
 return false;
 }
 else return !isBefore(d) ; //
 }
 //6. to determine this date is the nth day of its year.
 
 public int dayInYear(){
 int n=0;
 for( int=1; i<this.month; i++){
 n=daysInMonth(i,this.year)+n;   
 }
 n += this.day;
 return n;
 }
 //to calculate the difference of days between d and this date: 1.determine the days from 01/01/0001 t0 the d/this date(construct //the //dayInAll() 2. use the dayInAll of two days to get the difference.
 public int dayInAll() {
 
 int dayInAll = 0;
 int leapYearAmount = 0;
 
 for (int i = 1 ; i<yeaer ; i++)
 {  
   if (isLeapYear(i)
    {leapYearAmount++;
    }
    }
    dayInAll = (year - 1) *365 +leapYearAmount + dayInYear();
    return dayInAll;
    }
    public int difference(Date d) {
    int difference;
    difference = this.dayInAll() - d.dayInAll();
    return difference;
    }
     public static void main(String[] argv) {
    System.out.println("\nTesting constructors.");
    Date d1 = new Date(1, 1, 1);
    System.out.println("Date should be 1/1/1: " + d1);
    d1 = new Date("2/4/2");
    System.out.println("Date should be 2/4/2: " + d1);
    d1 = new Date("2/29/2000");
    System.out.println("Date should be 2/29/2000: " + d1);
    d1 = new Date("2/29/1904");
    System.out.println("Date should be 2/29/1904: " + d1);

    d1 = new Date(12, 31, 1975);
    System.out.println("Date should be 12/31/1975: " + d1);
    Date d2 = new Date("1/1/1976");
    System.out.println("Date should be 1/1/1976: " + d2);
    Date d3 = new Date("1/2/1976");
    System.out.println("Date should be 1/2/1976: " + d3);

    Date d4 = new Date("2/27/1977");
    Date d5 = new Date("8/31/2110");

    /* I recommend you write code to test the isLeapYear function! */

    System.out.println("\nTesting before and after.");
    System.out.println(d2 + " after " + d1 + " should be true: " + 
                       d2.isAfter(d1));
    System.out.println(d3 + " after " + d2 + " should be true: " + 
                       d3.isAfter(d2));
    System.out.println(d1 + " after " + d1 + " should be false: " + 
                       d1.isAfter(d1));
    System.out.println(d1 + " after " + d2 + " should be false: " + 
                       d1.isAfter(d2));
    System.out.println(d2 + " after " + d3 + " should be false: " + 
                       d2.isAfter(d3));

    System.out.println(d1 + " before " + d2 + " should be true: " + 
                       d1.isBefore(d2));
    System.out.println(d2 + " before " + d3 + " should be true: " + 
                       d2.isBefore(d3));
    System.out.println(d1 + " before " + d1 + " should be false: " + 
                       d1.isBefore(d1));
    System.out.println(d2 + " before " + d1 + " should be false: " + 
                       d2.isBefore(d1));
    System.out.println(d3 + " before " + d2 + " should be false: " + 
                       d3.isBefore(d2));

    System.out.println("\nTesting difference.");
    System.out.println(d1 + " - " + d1  + " should be 0: " + 
                       d1.difference(d1));
    System.out.println(d2 + " - " + d1  + " should be 1: " + 
                       d2.difference(d1));
    System.out.println(d3 + " - " + d1  + " should be 2: " + 
                       d3.difference(d1));
    System.out.println(d3 + " - " + d4  + " should be -422: " + 
                       d3.difference(d4));
    System.out.println(d5 + " - " + d4  + " should be 48762: " + 
                       d5.difference(d4));
  }
}
    
  
  
   
  
