#include <iostream>
#include <vector>
#include <climits>
#include <string>
#include <sstream>

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

string compressDP(const string& s) {
    int n = s.size();
    vector<int> dp(n + 1, INT_MAX);
    vector<string> compressed(n + 1, "");
    dp[0] = 0;

    for (int i = 1; i <= n; ++i) {
        for (int j = 0; j < i; ++j) {
            string comp = compressSegment(s, j, i - 1);
            int len = dp[j] + comp.length();

            if (len < dp[i]) {
                dp[i] = len;
                compressed[i] = compressed[j] + comp;
            }
        }

        if (compressed[i].length() >= s.substr(0, i).length()) {
            compressed[i] = s.substr(0, i);
            dp[i] = dp[i - 1] + 1;
        }
    }

    return compressed[n];
}

int main() {
    string input;

    while (true) {
        cout << "Enter a string to compress (or -1 to exit): ";
        getline(cin, input);

        if (input == "-1") {
            cout << "Exiting program." << endl;
            break;
        }

        string resultDP = compressDP(input);
        string finalResult = (resultDP.length() < input.length()) ? resultDP : input;

        cout << "Shortest Compression (DP): " << finalResult << endl << endl;
    }

    return 0;
}