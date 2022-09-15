# Keysight Eggplant on Sauce Labs





```shell
# install eggplant gateway
./epgw_setup

# setup configuration for chrome on windows
epgw add sauce-browser \
  --name saucelabs-chrome \
  --user ${SAUCE_USERNAME} \
  --apiKey ${SAUCE_ACCESS_KEY} \
  --dataCenter ${SAUCE_DC} \
  --platformName "Windows 10" \
  --browserName chrome \
  --browserVersion 104 \
  --screenResolution 1400x1050 \
  --url https://www.saucedemo.com


# setup configuration for device
epgw add sauce-device \
  --name saucelabs-iphone \
  --user ${SAUCE_USERNAME} \
  --apiKey ${SAUCE_ACCESS_KEY} \
  --dataCenter ${SAUCE_DC} \
  --platformName iOS \
  --deviceName "iPhone 8" \
  --app https://github.com/saucelabs/sample-app-mobile/releases/download/2.7.1/iOS.RealDevice.SauceLabs.Mobile.Sample.app.2.7.1.ipa

# start gateway
epgw vnc chrome --vncPort 5901 --webDriverPort 5001


```

https://eggplantsoftware.gitlab.io/products/connectivity/epgw/sauce-browsers/
https://eggplantsoftware.gitlab.io/products/connectivity/epgw/sauce-device/
git@github.com:keysight-eggplant/demo_scripts.git
git@github.com:keysight-eggplant/eggplant-github-action.git
https://docs.eggplantsoftware.com/gateway/sauce-overview/
https://eggplantsoftware.gitlab.io/products/connectivity/epgw/sauce-overview/
https://eggplantsoftware.gitlab.io/products/connectivity/epgw/sauce-device/

https://docs.eggplantsoftware.com/gateway/sauce-device/



[100]: https://eggplantsoftware.gitlab.io/products/connectivity/epgw/download/
[101]: https://www.eggplantsoftware.com/eggplant-functional-downloads



---


```shell
eggplant-studio
├── Eggplant.plist -> /Users/kareem/Library/Preferences/Eggplant.plist
├── libCache -> /Users/kareem/Library/Caches/Eggplant
├── libEggplant -> /Users/kareem/Library/Eggplant
└── logsApp -> /Users/kareem/Library/Logs/Eggplant
```


```shell


function epgwInstall () {
  epgwBaseDir="eggplant-gateway"
  epgwInstallDir="${epgwDir}/${epgwlatestVersion}"

  # create install directory
  [[ -d ${epgwInstallDir} ]] && return || mkdir ${epgwInstallDir}

  # extract
  mkdir ${epgwDir}/${epgwlatestVersion}
  tar xvzf bin/${epgwLatestFile} --directory ${epgwDir}/${epgwlatestVersion}

  # change mode and check
  chmod +x ./${epgwDir}/${epgwlatestVersion}/epgw
  epgwVersion=$(./${epgwDir}/epgw --version)
  [[ ${epgwVersion} ]] && printf "epgwVersion=%s\n" ${epgwVersion} || xattr -r -d com.apple.quarantine ${epgwDir}/.

  # add symlink to path and for latest
  ln -s -f ${epgwVersion} ./eggplant-gateway/latest
  [[ -f /usr/local/bin/epgw ]] || sudo ln -s -f ${PWD}/eggplant-gateway/latest/epgw /usr/local/bin/epgw

}


# get the latest macOS release details
epgwDownloadPage="https://eggplantsoftware.gitlab.io/products/connectivity/epgw/download/"
epgwDownloadData=$(curl -s ${epgwDownloadUrl})
epgwDownloadUrl=$(grep -o '<a .*href=.*>' <<< ${epgwDownloadData} | sed -e 's/<a /\n<a /g' | sed -e 's/<a .*href=['"'"'"]//' -e 's/["'"'"'].*$//' -e '/^$/ d' |grep osx)
epgwLatestFile="${epgwDownloadUrl##*/}"
epgwlatestVersion=$(awk -F'.' '{print $2"."$3"."$4}' <<< ${epgwLatestFile})

# download
[[ -d  bin ]] || mkdir bin
[[ -f bin/${epgwLatestFile} ]] || curl ${epgwDownloadUrl} --output bin/${epgwLatestFile}

# install
epgwInstall




```



[How to use sed get version number](https://unix.stackexchange.com/questions/531260/how-to-use-sed-get-version-number)
