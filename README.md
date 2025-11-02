#include <iostream>
#include <sstream>
#include <fstream>
#include <string>
#include <cstdlib>
#include <cmath>

using namespace std;

// Headers
string toString(double);
int toInt(string);
double toDouble(string);
double calcBreak(double fixedCost, double salesProject, int pageNum);

ifstream infile;

int main() {
    string bookTitle;
    double fixedCost, salesProject;
    int pageNum, rows;

    infile.open("book publishing.txt");
    for (rows = 1; rows <= 10; rows++) {
        cout << "Enter the title of the book" << endl;
        infile >> bookTitle;
        cout << bookTitle << endl;
        cout << "Reading sales projection" << endl;
        infile >> salesProject;
        cout << salesProject << endl;
        cout << "Enter perferred price" << endl;
        infile >> fixedCost;
        cout << fixedCost << endl;
        cout << "Reading number of pages" << endl;
        infile >> pageNum;
        cout << pageNum << endl;
    }
    infile.close();
    calcBreak(salesProject, fixedCost, pageNum);
    infile.open("book publishing.txt");
    while (!infile.eof()) {
        infile >> bookTitle;
        cout << bookTitle << endl;
    }
    infile.close();
    return 0;
}

double calcBreak(double fixedCost, double salesProject, int pageNum) {
    double breakevenPoint;
    int rows;

    fixedCost = 5.0;
    salesProject = 2345.67;
    cout << "Reading perferred price" << endl;
    cout << "Reading sales projection" << endl;
    cout << "Reading number of pages" << endl;
    cin >> pageNum;
    breakevenPoint = fixedCost + salesProject * pageNum * 1.05625 / salesProject;
    cout << "The break even point is " << breakevenPoint << endl;

    return breakevenPoint;
}

// The following implements type conversion functions.
string toString(double value) { //int also
    stringstream temp;
    temp << value;
    return temp.str();
}

int toInt(string text) {
    return atoi(text.c_str());
}

double toDouble(string text) {
    return atof(text.c_str());
}
