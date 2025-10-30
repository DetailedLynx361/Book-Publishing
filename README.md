#include <iostream>
#include <sstream>
#include <fstream>
#include <string>
#include <cstdlib>
#include <cmath>

using namespace std;

// Headers
string toString (double);
int toInt (string);
double toDouble (string);
double calcBreak(double fixedCost, double salesProject, int pageNum);

ifstream infile;
ofstream outfile;

int main()
{
    string bookTitle;
    double fixedCost, salesProject;
    int pageNum, rows;

    outfile.open("book publishing.txt");
    for (rows = 1; rows <= 1; rows++)
    {
        cout << "Enter the title of the book" << endl;
        cin >> bookTitle;
        outfile << bookTitle  << endl;
        cout << "Reading sales projection" << endl;
        cin >> salesProject;
        outfile << salesProject  << endl;
        cout << "Enter perferred price" << endl;
        cin >> fixedCost;
        outfile << fixedCost  << endl;
        cout << "Reading number of pages" << endl;
        cin >> pageNum;
        outfile << pageNum  << endl;
    }
    outfile.close();
    calcBreak(salesProject, fixedCost, pageNum);
    infile.open("book publishing.txt");
    while (!infile.eof())
    {
        infile >> bookTitle;
        cout << bookTitle << endl;
    }
    infile.close();
    return 0;
}

double calcBreak(double fixedCost, double salesProject, int pageNum)
{
    double breakevenPoint;
    int rows;

    cout << "Reading perferred price" << endl;
    cin >> fixedCost;
    cout << "Reading sales projection" << endl;
    cin >> salesProject;
    cout << "Reading number of pages" << endl;
    cin >> pageNum;
    breakevenPoint = fixedCost + salesProject * pageNum * 1.05625 / salesProject;
    cout << "The break even point is " << breakevenPoint << endl;
    
    return breakevenPoint;
}

// The following implements type conversion functions.
string toString (double value) { //int also
    stringstream temp;
    temp << value;
    return temp.str();
}

int toInt (string text) {
    return atoi(text.c_str());
}

double toDouble (string text) {
    return atof(text.c_str());
}
