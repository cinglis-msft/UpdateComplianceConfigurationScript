# The Update Compliance Configuration Script

This script is intended to configure devices to send data to Update Compliance, fulfilling all necessary requirements on the client. It can also be used for troubleshooting. 

## How this script is organized

This script is organized into two buckets: **Deployment** and **Pilot**. Both directories have the same key files -- `ConfigScript.ps1` and `RunConfig.bat`. You configure `RunConfig.bat` according to the directions in the `.bat` itself, which will then execute `ConfigScript.ps1` with the parameters entered to `RunConfig.bat`. 

* The **Deployment** portion of the script is intended to be deployed at-scale. It runs quietly, under the assumption that all devices are configured uniformly. However, 
* the **Pilot** portion of the script is intended to be tested on a limited number of devices and for troubleshooting. It is verbose, and saves logs according to the `logPath` variable in `RunConfig.bat`. The Pilot directory also has a Diagnostics directory with additional troubleshooting `.exe` files.


## How to use this script

When using this in the context of troubleshooting, use `Pilot`. Enter `RunConfig.bat`, and additionally do the following:

1. Configure `logPath` where you want the Logs to be output.
2. Configure `commercialIDValue` to your Commercial ID.
3. Run the script
4. Examine the Logs output for any issues. If there are no issues, then all devices with a similar configuration and network profile are ready for the Deployment script. 
5. If there are issues, gather the Logs and provide them to Support.


## Script errors


|Error  |Description  |
|---------|---------|
| 27    | Not system account. |
| 37    | Unexpected exception when collecting logs| 
| 1    | General unexpected error| 
| 6    | Invalid CommercialID| 
| 48    | CommercialID is not a GUID| 
| 8    | Couldn't create registry key path to setup CommercialID| 
| 9    | Couldn't write CommercialID at registry key path| 
| 53    | There are conflicting CommercialID values.| 
| 11    | Unexpected result when setting up CommercialID.| 
| 62    | AllowTelemetry registry key is not of the correct type REG_DWORD| 
| 63    | AllowTelemetry is not set to the appropraite value and it could not be set by the script.| 
| 64    | AllowTelemetry is not of the correct type REG_DWORD.| 
| 99    | Device is not Windows 10.| 
| 40    | Unexpected exception when checking and setting telemetry.| 
| 12    | CheckVortexConnectivity failed, check Log output for more information.| 
| 12    | Unexpected failure when running CheckVortexConnectivity.| 
| 66    | Failed to verify UTC connectivity and recent uploads.|  
| 67    | Unexpected failure when verifying UTC CSP.| 
| 41    | Unable to impersonate logged-on user.| 
| 42    | Unexpected exception when attempting to impersonate logged-on user.| 
| 43    | Unexpected exception when attempting to impersonate logged-on user.| 
| 16    | Reboot is pending on device, restart device and restart script.| 
| 17    | Unexpected exception in CheckRebootRequired.| 
| 44    | Error when running CheckDiagTrack service.| 
| 45    | DiagTrack.dll not found.| 
| 50    | DiagTrack service not running.| 
| 54    | Microsoft Account Sign In Assistant (MSA) Service disabled.| 
| 55    | Failed to create new registry path for SetDeviceNameOptIn| 
| 56    | Failed to create property for SetDeviceNameOptIn at registry path| 
| 57    | Failed to update value for SetDeviceNameOptIn| 
| 58    | Unexpected exception in SetrDeviceNameOptIn| 
| 59    | Failed to delete LastPersistedEventTimeOrFirstBoot property at registry path when attempting to clean up OneSettings.| 
| 60    | Failed to delete registry key when attempting to clean up OneSettings.| 
| 61    | Unexpected exception when attempting to clean up OneSettings.| 
| 52    | Could not find Census.exe| 
| 51    | Unexpected exception when attempting to run Census.exe| 
| 34    | Unexpected exception when attempting to check  Proxy settings.| 
| 30    | Unable to disable Enterprise Auth Proxy. This registry value must be 0 for UTC to operate in an authenticated proxy environment.| 
| 35    | Unexpected exception when checking User Proxy.| 


