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
