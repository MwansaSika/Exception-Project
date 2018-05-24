#include<iostream>
#include<string>
using namespace std;

//defining class Employee
class Employee
{
private:
	string Emp_Name;
	int Emp_Number;
	string Emp_Hiredate;

public:   
	Employee() //Default constructor
{
	Emp_Name = " ";
	Emp_Number = 0;
	Emp_Hiredate = " ";
}
//Constructor Parameters
 Employee(string name, int number, string date)
		  {
			  Emp_Name = name;
			  Emp_Number = number;
			  Emp_Hiredate = date;
		  }
		//Exception class for Invalid ID
		  class InvalidEmployeeNumber
		  {
		  };
		  //Getters and Setters
		  void setEmpName(string);
		  void setEmpNumber(int);
		  void setHireDate(string);
		  string getEmpName();
		  int getEmpNumber();
		  string getHireDate();
}; // End of employ class defining

   //Defining of setters and getters
void Employee::setEmpName(string name)
{
	Emp_Name = name;
}
void Employee::setEmpNumber(int number)
{
	if (number<0 || number>9999)
		throw InvalidEmployeeNumber();
	else
		Emp_Number = number;
}
void Employee::setHireDate(string date)
{
	Emp_Hiredate = date;
}
string Employee::getEmpName()
{
	return Emp_Name;
}
int Employee::getEmpNumber()
{
	return Emp_Number;
}
string Employee::getHireDate()
{
	return Emp_Hiredate;
}//end of setters and getters

 //Derived class ProductionWorker
class ProductionWorker :public Employee
{

private:int Shift;
		double HourlyPay;
		//Default constructor
public: ProductionWorker()
{
	Shift = 0;
	HourlyPay = 0.0;
}
		//Parameter constructor
		ProductionWorker(int shft, double pay)
		{
			Shift = shft;
			HourlyPay = pay;
		}
		//Exception class for Invalid shift
		class InvalidShift {};
		//Exception class for Invalid Pay rate
		class InvalidPayRate {};
		void setShift(int);
		void setHourlyPay(double);
		int getShift();
		double getHourlyPay();
};

//Defining member functions
void ProductionWorker::setShift(int shft)
{
	if (shft<0 || shft>2)
		throw InvalidShift();
	else
		Shift = shft;
}
void ProductionWorker::setHourlyPay(double pay)
{
	if (pay<1)
		throw InvalidPayRate();
	else
		HourlyPay = pay;
}
int ProductionWorker::getShift()
{
	return Shift;
}
double ProductionWorker::getHourlyPay()
{
	return HourlyPay;
}//end of setters and getters



int main()
{ 
	int shift;
	double pay;
	

	cout << " 1-DayShift \n\ 2-Night \n" << endl;
	cout << "Enter shift: ";
	cin >> shift;
	cout << "Enter hourly pay: ";
	cin >> pay;

	ProductionWorker pw(0, 0);

	pw.setEmpName("Mwansa");
	pw.setHireDate(" 17th July");
	try
	{
		pw.setEmpNumber(1000);
		pw.setShift(shift);
		pw.setHourlyPay(pay);

	}
	catch (Employee::InvalidEmployeeNumber)
	{
		cout << "Sorry! wrong Employee number\n" << endl;
	}
	catch (ProductionWorker::InvalidShift)
	{
		cout << "Sorry! inputted wrong Shift\n" << endl;
	}
	catch (ProductionWorker::InvalidPayRate)
	{
		cout << "Sorry! wrong pay Rate\n" << endl;
	}

	cout << "\n-----------------";
	cout << "\nEmployee Details:" << endl;
	cout << "-----------------\n";
	cout << "\nName: " << pw.getEmpName() << endl;
	cout << "Number: " << pw.getEmpNumber() << endl;
	cout << "Hire Date: " << pw.getHireDate() << endl;
	cout << "Shift: " << pw.getShift() << endl;
	cout << "Hourly Pay: " << pw.getHourlyPay() << endl;
	cout << "----------------" << endl;


	
	cin.get();
	cin.get();
	return 0;
}
