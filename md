/* PROGRAM: NAME
By Nate Townsell 2019
This program does...
*/

#include<iostream>
#include<cmath>
#include<iomanip>     //stream manipulators like set precision, setw(n)
#include<string>     //strings
#include<cstdlib>     // used for the rand(); function
#include<ctime>      //for the time function time(0). This function returns the number of seconds that have elapsed since Jan 1 1970
#include<fstream>    //for C++ file access
#include<cstring>
using namespace std;

class Movie
{
	public:
	string name;
	int length;
	string genre;
	double rentalprice;
};

class MovieRentalDatabase
{
	int parameter;
	Movie *movie;
	public :
	MovieRentalDatabase()
	{}
	MovieRentalDatabase(int var)
	{
	parameter = var;
	movie = new Movie[parameter];
	}
void initialize()
{
for(int i=0;i<parameter;i++)
{cout<<"Please enter the data for movie #"<<i+1<<"\n";
cout<<"Name: ";
cin>>movie[i].name;
cout<<"Length(in mintues): ";
cin>>movie[i].length;
cout<<"Genre: ";
cin>>movie[i].genre;
cout<<"Prices(in dollars and cents format): ";
cin>>movie[i].rentalprice;
}
}
void show()
{
for(int i=0;i<parameter;i++)
{
cout<<movie[i].name<<"\t"<<movie[i].length<<"\t"<<movie[i].genre<<"\t"<<movie[i].rentalprice<<"\n";
}
}
void change()
{
string name;
cout<<"enter the movie name to change content: ";
cin>>name;
int i=0;
while(name!=movie[i].name)
{
++i;
}
if(i==parameter)
{
cout<<"Wrong name is entered";}
else
{
cout<<"enter the new content\n";
cout<<"Enter the updated movie name: ";
cin>>movie[i].name;
cout<<"Enter the updated length of movie: ";
cin>>movie[i].length;
cout<<"Enter the updated genre of movie: ";
cin>>movie[i].genre;
cout<<"Enter the new rental price of movie: ";
cin>>movie[i].rentalprice;
}
}

void ascendingsort()
{
Movie temp;
for (int i=1;i<parameter;i++){
for(int j=1;j<parameter;j++)
{
if(movie[j-1].name>movie[j].name)
{
temp = movie[j-1];
movie[j-1]=movie[j];
movie[j]=temp;
}
}
}
}
void descendingsort()
{
Movie temp;
for (int i=parameter-1;i>0;i--){
for(int j=parameter-1;j>0;j--)
{
if(movie[j-1].name<movie[j].name)
{
temp = movie[j-1];
movie[j-1]=movie[j];
movie[j]=temp;
}
}
}
}
};
int main()
{
int num=4;
int n;
bool choice=true;
MovieRentalDatabase *database;
while(choice)
{
cout<<"Welcome to movie\n";
cout<<"Please Select One\n"<<"1) Enter all movie data into array\n"<<"2)Display all movie data currently in array \n"<<"3) change the content of anyone array element\n"<<"4) Sort the array by movie name in ascending order\n"<<"5) Sort the array by movie name in descending order\n"<<"6) Quit: ";
cin>>n;
cout<<"Selection "<<n<<"\n";
switch(n){
case 1:
cout<<"how movie you want to enter: ";
cin>>num;

database = new MovieRentalDatabase(num);

database->initialize();
break;
case 2:
cout<<"the list is: \n";
database->show();
break;
case 3:
database->change();
break;

case 4:
cout<<"ascending order: \n";
database->ascendingsort();
break;
case 5:
cout<<"descending order is: \n";
database->descendingsort();
break;
case 6:
choice = false;
break;
default :
cout<<"wrong choice\n";
}
}
return 0;

}
