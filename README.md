

Source code in C++ :  
#include <bits/stdc++.h> 
using namespace std; 
#define go cout<<'\n' 
#define OR || 
#define AND && 
string hari[7] = {"Senin", "Selasa", "Rabu", "Kamis", "Jumat", "Sabtu",  "Minggu"}; 
int count_day(int month, int year){ 
int count; 
if(month == 1 OR month == 3 OR month == 5 OR month == 7 OR month == 8 OR month == 10 OR month == 12) count = 31; 
else if(month == 4 OR month == 6 OR month == 9 OR month == 11) count =  30; 
else{ 
if(year %400 == 0) count = 29; 
else if(year%100 == 0) count = 28; 
else if(year %4 == 0 ) count = 29; 
else count = 28; 
} 
return count; 
} 
bool isKabisat(int year){ 
if(year %400 == 0) return true; 
else if(year%100 == 0) return false; 
else if(year %4 == 0 ) return true; 
else return false; 
}
int main(){ 
int tanggal,bulan,tahun; 
cout << "Input tanggal,bulan, dan tahun : "; cin >> tanggal >> bulan >> tahun; 
int total_day,day; 
total_day = 365*(tahun-1); 
if(tanggal > count_day(bulan,tahun) || bulan >12){ 
cout << "Invalid\n"; 
return 0; 
} 
for(int i = 0; i < tahun; ++i){ 
if(isKabisat(i)) total_day++; 
} 
for(int i = 0; i <=bulan; ++i){ 
if(i<=7 AND i != bulan){ 
if(i%2==0 AND i!=2) total_day+=30; 
else if(i%2 !=0) total_day+=31; 
else if(i == 2) total_day+=28; 
}else if(i > 7 AND i!=bulan){ 
if(i%2==0) total_day+=31; 
else total_day+=30; 
} 
if(i==bulan) total_day+=tanggal; 
} 
day = (total_day + 3)%7; 
cout << hari[day]; 
}
