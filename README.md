# Amd-AI9-HX-370
Settings for the Amd-AI9-HX-370

## Radeon Software Context Menu Issue
 The Radeon Adrenaline software seems to launch on mouse right click.  I seem to have corrected with the following registry settings
 
 ```
 [HKEY_LOCAL_MACHINE\SOFTWARE\Classes\PackagedCom\Package\AdvancedMicroDevicesInc-RSXCM_22.10.0.0_x64__v2es6h43hjn86\Server\0]
"ApplicationId"="AMDRadeonSoftwareDesktop"
"ApplicationDisplayName"="@{AdvancedMicroDevicesInc-RSXCM_22.10.0.0_x64__v2es6h43hjn86?ms-resource://AdvancedMicroDevicesInc-RSXCM/Resources/AppDisplayName}"
"DisplayName"="Catalyst Context Menu extension"
"Executable"="_radeonsoftware.exe"
"IsSystemExecutable"=dword:00000000
"Arguments"="-ToastActivated"
"TrustLevel"=dword:00000001
"RuntimeBehavior"=dword:00000001
"BnoIsolation"=dword:00000000
"SurrogateAppId"="{FDADFEE3-02D1-4E7C-A511-380F4C98D73B}"
 ```

 In this case I changed *Executable"="_radeonsoftware.exe* to have an underscore in the *radeonsoftware.exe*. This prevents the application from running and is easy to restore if needed.
