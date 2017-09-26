Pluggable Authentication Module using Touch-ID
----------------------------------------------

This module allows us to authenticate services via touch-id using Apple's
`LocalAuthentication` API. I am using the module to authenticate `sudo` as it's
something we run frequently. The module can be dropped in to authenticate any
other PAM enabled service as well.

Compilation
-----------

Compile this module as the user who has touchid active. Otherwise manually edit
the user id's inside the .m file.


`make all`


Copy the module `sudo cp pam_touchid.so /usr/local/lib/`, may need to create directory.

Next, add this line to the top of `/etc/pam.d/sudo` 

```
auth       sufficient     /usr/local/lib/pam_touchid.so
```

This also allows fallback to standard password authentication if your finger
fails.


Screenshot
----------


Here's what shows on the touchbar when you try to `sudo` with the module
installed

![Touchbar screenshot](tscrot.png)

