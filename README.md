# names-scores
You are given around five-thousand first names, begin by sorting it into alphabetical order. Then working out the alphabetical value for each name, multiply this value by its alphabetical position in the list to obtain a name score.

For example, when the list in sample is sorted into alphabetical order, PAMELA, which is worth , is the  name in the list. So, PAMELA would obtain a score of .

You are given  queries, each query is a name, you have to print the score.

Input Format

The first line contains an integer , i.e., number of names.
Next  lines will contain a Name.
Followed by integer  followed by  lines each having a word.

Constraints

length of each word will be less than 
Output Format

Print the values corresponding to each test case.

Sample Input

5
ALEX
LUIS
JAMES
BRIAN
PAMELA
1
PAMELA
Sample Output

240
Explanation

Explained in statement.

#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
#include <map>

using namespace std;

map<string, int> nameVals;
map<string, int> namePos;

int main() 
{
    int n;
    cin >> n;

    vector<string> names(n);
    
    for(int i=0; i<n; i++)
    {
        string name;
        cin >> name;

        names[i] = name;
            
        for(auto c : name)
        {
            int worth = (int)c - 64;
            nameVals[name] += worth;
        }                
    }
    sort(names.begin(), names.end());
   
    for(int i=0; i<n; i++)
    {
        namePos[names[i]] = i+1;
    }
    
    int q;
    cin >> q;
    
    while(q--)
    {
        string query;
        cin >> query;
                
        cout << nameVals[query] * namePos[query] << endl;
    }
    return 0;
}
