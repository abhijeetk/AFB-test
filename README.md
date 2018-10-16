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
```

2. Binding libraries on target
```
root@m3ulcb:/# find . -name *.so | grep binding 
./usr/lib/python3.5/site-packages/_dbus_bindings.so
./usr/lib/python3.5/site-packages/_dbus_glib_bindings.so
./var/local/lib/afm/applications/agl-service-gps/1.0/lib/libafm-gps-binding.so
./var/local/lib/afm/applications/agl-service-mediaplayer/1.0/lib/libafm-mediaplayer-binding.so
./var/local/lib/afm/applications/agl-service-bluetooth/1.0/lib/libafm-bluetooth-binding.so
./var/local/lib/afm/applications/agl-service-geofence/1.0/lib/libafm-geofence-binding.so
./var/local/lib/afm/applications/agl-service-mediascanner/1.0/lib/libafm-mediascanner-binding.so
./var/local/lib/afm/applications/nfc-binding/0.1/lib/afb-nfc-binding.so
./var/local/lib/afm/applications/agl-service-wifi/1.0/lib/libafm-wifi-binding.so
./var/local/lib/afm/applications/agl-service-radio/1.0/lib/libafm-radio-binding.so
./var/local/lib/afm/applications/persistence-binding/0.1/lib/afb-persistence-binding.so
./var/local/lib/afm/applications/hvac/0.1/lib/libhvac-demo-binding.so
./var/local/lib/afm/applications/agl-service-geoclue/1.0/lib/libafm-geoclue-binding.so
./var/local/lib/afm/applications/agl-identity-service/0.1/lib/afb-identity-binding.so
./var/local/lib/afm/applications/naviapi-binding-service/0.1/lib/libNaviAPIService.so
./var/local/lib/afm/applications/phone/0.1/lib/libtelephony-binding.so
```

3. All websockets available to <uid> with smack access (here *)

```
root@m3ulcb:/# ls -Z ./run/user/0/apis/ws
* Bluetooth-Manager  * identity      * nfc                wifi-manager
* geoclue            * low-can       * persistence	     * windowmanager
* geofence           * mediaplayer   * radio
* gps                * mediascanner  * signal-composer
* homescreen         * naviapi       * unicens
```
