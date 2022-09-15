# Eggplant Gateway for Sauce Labs




<img align="right" src="assets/sauce-logo.png">  


### :rocket: [Sign Up for a _free_ trial at Sauce Labs][000] :bangbang:

<br>

### Read
  - [Sauce Labs Integration for Eggplant Gateway][101]


#### Configure
  - [Sauce Labs Browsers][104]
  - [Sauce Labs Devices][105]



<br><br><br>

```shell
# clone repo
git clone git@github.com:kmissoumi/quick-sauce-eggplant-gateway.git
cd quick-sauce-eggplant-gateway


# export environment variables
export SAUCE_USERNAME=
export SAUCE_ACCESS_KEY=
export SAUCE_DC="eu-central-1"        # us-west-1


# install eggplant gateway
chmod +x && ./epgw_setup


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
epgw vnc saucelabs-chrome --vncPort 5901 --webDriverPort 5001
```

<br>


#### Download
  - [Eggplant Gateway][102]
  - [Eggplant Functional][103]

<br>



_This source code is licensed under the MIT license found in the LICENSE file in the root directory of this source tree._


[101]: https://eggplantsoftware.gitlab.io/products/connectivity/epgw/sauce-overview/
[102]: https://eggplantsoftware.gitlab.io/products/connectivity/epgw/download/
[103]: https://www.eggplantsoftware.com/eggplant-functional-downloads
[104]: https://eggplantsoftware.gitlab.io/products/connectivity/epgw/sauce-browsers/
[105]: https://eggplantsoftware.gitlab.io/products/connectivity/epgw/sauce-device/

[201]: git@github.com:keysight-eggplant/demo_scripts.git
[202]: git@github.com:keysight-eggplant/eggplant-github-action.git

[301]: https://docs.eggplantsoftware.com/gateway/sauce-overview/

[000]: https://saucelabs.com/sign-up
