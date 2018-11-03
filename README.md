# Complex-numbers-operations-C---operator-overloading
multiple operations on complex numbers in C++ with overloading operator
//Eng Aseel Taher

#include <iostream>
#include<math.h>
using namespace std;

class Complex
{
    friend Complex operator+(Complex &,Complex &);
    friend Complex operator-(Complex &,Complex &);
private:
    double real,imag;
public:

    Complex(double real=2,double imag=2):real(real),imag(imag){}

    void setter()
    {
        cout<<"enter the real and imaginary part"<<endl;
        cin>>real>>imag;
    }
    void getter()
    {
        cout<<"( "<<real<<" , "<<imag<<" )\n"<<endl;

    }
    Complex multi(Complex &obj)
    {
        Complex sum;
        sum.real=obj.real*real-imag*obj.imag;
        sum.imag=real*obj.imag+imag*obj.real;
        return sum;
    }
    Complex div(Complex &obj)
    {
        double domen;
        domen=pow(obj.real,2)+pow(obj.imag,2);
        obj.imag=-1*obj.imag;
        Complex sum;
        sum.real=(real*obj.real-imag*obj.imag)/domen;
        sum.imag=(real*obj.imag+imag*obj.real)/domen;
        return sum;
    }


};

Complex operator+(Complex &obj,Complex &obj1)
{
    return Complex(obj1.real+obj.real,obj1.imag+obj.imag);
}
Complex operator-(Complex &obj,Complex &obj1)
{
    return Complex(obj.real-obj1.real,obj.imag-obj1.imag);
}

int main()
{

    Complex obj1;
    obj1.setter();
    Complex obj2;
    obj2.setter();
    Complex sum1;
    //----------------
    sum1=obj1+obj2;
    cout<<"The sum is ->> "<<endl;
    sum1.getter();
    sum1=obj1-obj2;
    cout<<"The sub is ->> "<<endl;
    sum1.getter();
    sum1=obj1.multi(obj2);
    cout<<"The multiplication is ->> "<<endl;
    sum1.getter();
    sum1=obj1.div(obj2);
    cout<<"The division is ->> "<<endl;
    sum1.getter();
    return 0;
}
