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
8. Run the script in a Xcode Playground / online swift compiler
9. See the terminal output

**Script:**
```
import Foundation

var data = """
iOS 14.5.1,327524
iOS 15.0.1,528090
iOS 14.3,524143
iOS 15.0,38215
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
"""

/*
TotalUsers : Total users who have used app within the given timeframe
TotalSupportedUsers : Subset from TotalUsers who lie withing minSupportedVersion & currentVersion
*/

let lines = data.split { $0.isNewline }

let minSupportedVersion = "11"
let currentVersion = "15"

var totalUsers = 0
var totalSupportedUsers = 0

var supportedUsersDictionary: [String: Int] = [:]

for line in lines {
    let iOSVersion: String = String(line.split(separator: ".").first!).lowercased()
    let userCount: Int = Int(line.split(separator: ",")[1])!
    totalUsers += userCount
    let versionNumber: String = String(iOSVersion.split(separator: " ")[1])
    if versionNumber <= currentVersion && versionNumber >= minSupportedVersion {
        totalSupportedUsers += userCount
        supportedUsersDictionary[iOSVersion, default: 0] += userCount
    }
}

print("Total Users: \(totalUsers)")
print("Total Supported Users: \(totalSupportedUsers)\n")
print("Supported Version Distribution")

for (iOSVersion, numberOfUsers) in supportedUsersDictionary {
    let percent = String(format: "%.2f", Double(numberOfUsers) / Double(totalSupportedUsers) * Double(100))
    print("\(iOSVersion): \(percent)%")
}
```

**Sample Output:**
```
 Total Users: 1542866
 Total Supported Users: 1541347
 
 Supported Version Distribution
 ios 11: 0.18%
 ios 12: 3.13%
 ios 13: 7.17%
 ios 14: 89.52%
```
