#include <iostream>
#include <string>
using namespace std;

string compressSegment(const string& s, int start, int end) {
    string result = "";
    int count = 1;
    for (int i = start + 1; i <= end; ++i) {
        if (s[i] == s[i - 1]) {
            count++;
        }
        else {
            result += s[i - 1] + to_string(count);
            count = 1;
        }
    }
    result += s[end] + to_string(count);
    return result;
}

string compressBruteForce(const string& s) {
    int n = s.length();
    string bestCompression = s;
    int bestLength = n;

    for (int i = 1; i < n; ++i) {
        string left = s.substr(0, i);
        string right = s.substr(i);

        string leftCompressed = compressSegment(s, 0, i - 1);
        string rightCompressed = compressSegment(s, i, n - 1);

        string combined = leftCompressed + rightCompressed;

        if (combined.length() < bestLength) {
            bestCompression = combined;
            bestLength = combined.length();
        }
    }

    string fullCompressed = compressSegment(s, 0, n - 1);
    if (fullCompressed.length() < bestLength) {
        bestCompression = fullCompressed;
    }

    return bestCompression;
}

int main() {
    while (true) {
        string input;
        cout << "Enter a string to compress (or -1 to exit): ";
        getline(cin, input);

        if (input == "-1") {
            cout << "Exiting program." << endl;
            break;
        }

        string resultBrute = compressBruteForce(input);

        string finalResult = (resultBrute.length() < input.length()) ? resultBrute : input;

        cout << "Shortest Compression (Brute Force): " << finalResult << endl;
    }
    return 0;
}