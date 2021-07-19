# Firebase-Version-Analytics-iOS

**Get iOS Version Analytics from Firebase**

**How to:**
1. Go in the Firebase Analytics Dashboard
2. Filter iOS Platform only
3. Scroll down, select `Device` under the "What is your audience like?" widget
4. Export the CSV data (top right corner, there's a download button with Download CSV option)
5. Open the file and select the iOS breakdown raw data
6. Replace your data with the sample data in this script
7. Set `minSupportedVersion` and `currentVersion` as per requirement
8. Run the script in a Xcode Playground
9. See the terminal output

**Sample Input:**
iOS 14.5.1,327524
iOS 14.2,528090
iOS 14.3,524143
iOS 13.1.3,38215
iOS 13.1.3,14333
iOS 13.2.3,12667
iOS 13.2.3,9568
iOS 12.4.1,18392
iOS 13.2.2,6816
iOS 13.2,14352
iOS 12.4.9,12694
iOS 13.1.2,6652
iOS 13.2,5439
iOS 12.4.2,4008
iOS 12.4.3,3715
iOS 12.4.1,3111
iOS 12.3.1,3021
iOS 13.1.2,2514
iOS 12.4.3,2455
iOS 10.1,390
iOS 8.4,24
iOS 9.3.2,23
iOS 9.3.6,123
iOS 9.3.3,22
iOS 11.0,1462
iOS 11.0.2,1310
iOS 12.3.2,866
iOS 9.2,19
iOS 10.0,918

**Sample Output**
Total Users: 1542866
Total Supported Users: 1541347

Supported Version Distribution
ios 13: 7.17%
ios 14: 89.52%
ios 12: 3.13%
ios 11: 0.18%
