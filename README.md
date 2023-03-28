# Sorted-Sums-Hackerrank-Leetcode-c-
#include <bits/stdc++.h> 
using namespace std; 

int solve(vector<int> v, int n) {
    long long ans = 0, M = 1e9 + 7;
    for(int i = 0; i < n; i++) {
        int j = i;
        while(j > 0 && v[j - 1] > v[j]) {
            swap(v[j], v[j - 1]);
            j--;
        }
        for(int j = 0; j <= i; j++) {
            ans = (ans + v[j] * 1ll * (j + 1)) % M;
        }
        ans %= M;
    }
    return ans;
}

int main() {
    int n;
    cin >> n;
    vector<int> v(n);
    for(int i = 0; i < n; i++) {
        cin >> v[i];
    }
    cout << solve(v, n);
}
