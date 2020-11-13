# Gray-code
Gray code is a binary code where each successive value differs in only one bit, as well as when wrapping around. Gray code is common in hardware so that we don't see temporary spurious values during transitions.  Given a number of bits n, generate a possible gray code for it.  For example, for n = 2, one gray code would be [00, 01, 11, 10].


#include <bits/stdc++.h>
using namespace std;
 
// This function generates all n 
// bit Gray codes and prints the
// generated codes
vector<string> generateGray(int n)
{
    // Base case
    if (n <= 0)
        return {"0"};
 
    if (n == 1)
    {
      return {"0","1"};
    }
 
    //Recursive case
    vector<string> recAns=
          generateGray(n-1);
    vector<string> mainAns;
     
    // Append 0 to the first half
    for(int i=0;i<recAns.size();i++)
    {
      string s=recAns[i];
      mainAns.push_back("0"+s);
    }
     
     // Append 1 to the second half
    for(int i=recAns.size()-1;i>=0;i--)
    {
       string s=recAns[i];
       mainAns.push_back("1"+s);
    }
    return mainAns;
}
 
// Function to generate the 
// Gray code of N bits
void generateGrayarr(int n)
{
    vector<string> arr;
    arr=generateGray(n);
    // print contents of arr 
    for (int i = 0 ; i < arr.size();
         i++ )
        cout << arr[i] << endl;
}
 
// Driver Code
int main()
{
    generateGrayarr(3);
    return 0;
}
