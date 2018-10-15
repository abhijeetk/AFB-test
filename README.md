# AFB-test

Code for this application is taken from:

https://git.automotivelinux.org/src/app-framework-binder/tree/test/AFB.html

https://git.automotivelinux.org/src/app-framework-binder/tree/test/AFB.js

#### Steps to install
1. Create wgt:

user@user-P5530: <AGL_SRC>/build/tmp/sysroots-components/x86_64/af-main-native/usr/bin/wgtpkg-pack /path/to/AFB-test -o AFB-test.wgt
  
2. Push wgt to target

user@user-P5530: scp AFB-test.wgt root@ip-addr:~
  
3. Login to target

4. Go to /home/root folder

5. Install wgt

root@m3ulcb:~# afm-util install AFB-test.wgt

### TIPS :
1. All running binders 

root@m3ulcb:~/# ps -ef | grep afb
```
root      4379  4274  0 19:02 ?        00:00:00 afbd-windowmanager-service-2017@0.1
root      4381  4274  0 19:02 ?        00:00:00 afbd-agl-service-wifi@1.0          
root      4383  4274  0 19:02 ?        00:00:00 afbd-agl-service-bluetooth@1.0     
root      4385  4274  0 19:02 ?        00:00:00 afbd-agl-service-unicens@0.1       
root      4394  4274  0 19:02 ?        00:00:00 afbd-agl-identity-service@0.1      
root      4396  4274  0 19:02 ?        00:00:00 afbd-homescreen-2017@0.1           
root      4398  4274  0 19:02 ?        00:00:00 afbd-homescreen-service-2017@0.1   
root      4399  4274  0 19:02 ?        00:00:00 afbd-persistence-binding@0.1       
root      4429  4274  0 19:02 ?        00:00:00 afbd-nfc-binding@0.1               
root      4917  4274  0 19:46 ?        00:00:00 afbd-mediaplayer@0.1               
root      4923  4274  0 19:46 ?        00:00:00 afbd-agl-service-mediaplayer@1.0   
root      4928  4274  0 19:46 ?        00:00:00 afbd-agl-service-mediascanner@1.0  
root      4943  4274  0 19:46 ?        00:00:00 afbd-ws-test-igalia@1.0            
root      4956  4274  0 19:46 ?        00:00:00 afbd-signal-composer@4.0           
root      4960  4274  0 19:46 ?        00:00:00 afbd-naviapi-binding-service@0.1   
root      4962  4274  0 19:46 ?        00:00:00 afbd-low-can-service@5.0           
root      4964  4274  0 19:46 ?        00:00:00 afbd-agl-service-geoclue@1.0       
root      5144  4855  0 19:50 ttySC0   00:00:00 grep afb
```
1. All websockets available to <uid> with smack access (here *)

```
root@m3ulcb:/# ls -Z ./run/user/0/apis/ws  
* Bluetooth-Manager  * identity      * nfc                wifi-manager
* geoclue            * low-can       * persistence	     * windowmanager
* geofence           * mediaplayer   * radio
* gps                * mediascanner  * signal-composer
* homescreen         * naviapi       * unicens
```