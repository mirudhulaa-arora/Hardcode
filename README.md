# Hardcode
#include <iostream>
using namespace std;

int MinEmpExp(int emp_exp)
{
    int CostperHr;
    if(emp_exp<2 && emp_exp>=0)     CostperHr=100;
    else if(emp_exp<6 && emp_exp>=2)    CostperHr=150;
    else if(emp_exp<10 && emp_exp>=6)    CostperHr=200;
    else if(emp_exp>=10)    CostperHr=250;
    //cout<<CostperHr<<endl;
    return CostperHr;
}

int Increment(int Sat_Sun)
{
    int inc_amt = 0.05 * Sat_Sun;
    //cout<<inc_amt<<endl;
    return inc_amt;
}

int CalcTotalCost(int emp_exp, int empWorkHrs[])
{
    int i, Sat_Sun=0, Mon_Fri=0, Total_Cost, Inc_Per, Final_Sat_Sun=0;
    for(i=0; i<7; i++)
    {
        //cout<<i<<endl;
        if(i==5 || i==6)
        {
            Sat_Sun = empWorkHrs[i] * MinEmpExp(emp_exp);
            //cout<<Sat_Sun<<endl;
            Inc_Per = Increment(Sat_Sun);
            //cout<<Inc_Per<<endl;
            Final_Sat_Sun = Final_Sat_Sun + Sat_Sun + Inc_Per;
            //cout<<Final_inc_amt<<endl;
            
        }
        else
        {
            Mon_Fri = Mon_Fri + empWorkHrs[i] * MinEmpExp(emp_exp);
            //cout<<Mon_Fri<<endl;
        }
    }
    Total_Cost = Final_Sat_Sun + Mon_Fri;
    //cout<<Total_Cost<<endl;
    return Total_Cost;
}

int main()
{
    int emp_exp,i,TOTAL_COST;
    int empWorkHrs[7];
    cout<<"Enter min exp : ";
    cin>>emp_exp;
    cout<<"\nEnter work hours : "<<endl;
    for(i=0;i<7;i++)
        cin>>empWorkHrs[i];
    TOTAL_COST = CalcTotalCost(emp_exp,empWorkHrs);
    cout<<"____________________________\n\n";
    cout<<"COST = "<<TOTAL_COST;
    return 0;
}



