// integral_function

//arb2019_integral_function

#include "stdafx.h"

#include<iostream>

#include<fstream>

#include<cmath>

#include<iomanip>

#include<cstring>

using namespace std;

const int lengthColumn=20;

const int Indent=7;

const int lengthTable=43;

//////////////////////////

double Fi(double x)

{

return cos(x)*cos(x);

}

///////////////////////////////

double Psi(double x)

{

return (1-x*x)/(1+x*x);

}

/////////////////////////

double F(double x,double t)

{

return Psi(x)*Fi(x+ t/(1+x*x));

}

///////////////////////////////////////

void create(ifstream &f, double x[], int n)

{

int i;

for(i=0;i<n;i++) f>>x[i];

}

/////////////////////////////////////////

void show(ofstream &f, double x[], int n)

{

int i;

for(i=0;i<n;i++)

f<<x[i]<<' ';

f<<endl;

}

/////////////////////////////////////////

double Integral(double a, double b, double e, double t)

{

double h,J1,J2;

int i,n;

n=1; h=(b-a)/n;

J2=h*F(a+h/2, t);

do

{

J1=J2;

n=n*2;

h=(b-a)/n;

J2=0;

for (i=0;i<=n-1;i++)

J2=J2+F(a+(2*i+1)*h/2,t);

J2=J2*h;

}while (fabs(J2-J1)>e);

return J2;

}

//////////////////////////////////////

void star(ofstream &f, int n, int m)

{

f.width(n);

int i;

for(i=0;i<m;i++)

f<<'*';

f<<endl;

}

/////////////////////////////////////

void star1(ofstream &f, int n, int m)

{

f.width(n); f<<'*';

int i;

for(i=0;i<m;i++)

{

f.width(lengthColumn+1);

f<<'*';

}

f<<endl;

}

//////////////////////////////////////

void table(ofstream &f,double* x,double* y,int m, char a[2][15])

{

int i;

f<<endl;

star(f,Indent+1,lengthTable);

star1(f,Indent+1,2);

f.width(Indent+1);

f<<'*';

for(i=0;i<2;i++)

{

f.width(10);

f<<a[i];

f.width(11);

f<<'*';

}

f<<endl;

star1(f,Indent+1,2);

star(f,Indent+1,lengthTable);

for(i=0;i<m;i++)

{

star1(f,Indent+1,2);

f.width(Indent+1);

f<<'*';

f.width(lengthColumn-5);

f<<x[i];

f.width(6);

f<<'*';

f.width(lengthColumn-5);

f<<y[i];

f.width(6);

f<<'*';

f<<endl;

star1(f,Indent+1,2);

star(f,Indent+1,lengthTable);

}

}

/////////////////////////////

int main()

{

ifstream in("arb.txt");

ofstream out("integral.txt");

double a,b,eps;

int m,i;

char name_task[80];

char name_x_y[2][15];

in.getline(name_task,80);

for(i=0;i<2;i++)

in>>name_x_y[i];

out<<name_task<<endl;

for(i=0;i<2;i++)

out<<name_x_y[i]<<' ';

out<<endl;

in>>a>>b>>eps>>m;

out<<"a= "<<a<<endl;

out<<"b= "<<b<<endl;

out<<"eps= "<<eps<<endl;

out<<"m= "<<m<<endl;

double* t, *y;

t=new double[m];

y=new double[m];

create(in, t,m);

out<<"arguments : "<<endl;

show(out,t,m);

for(i=0;i<m;i++)

y[i]=Integral(a,b,eps,t[i]);

out<<"value of integeral"<<endl;

show(out,y,m);

out<<endl;

out<<setw(15+strlen(name_task))<<name_task<<endl;

table(out,t,y,m,name_x_y);

in.close();

out.close();

delete []t;

delete []y;

system("pause");

return 0;

}
