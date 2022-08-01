{
   "version": "1.0",
- Json deferred maintenance version
   "systemType": "xxx",
   "serviceableEvent": {
      "cecErrorLog": {
         "errPel": "xxx",
- Platform event log id associated with servicable event
- tail of object /xyz/openbmc_project/logging/entry/968
         "src": "xxx",
- System reference code of pel
- busctl get-property xyz.openbmc_project.Logging /xyz/openbmc_project/logging/entry/968  xyz.openbmc_project.Logging.Entry EventId
- s "BC50E504 000000E0 00000B00 00000000 00200000 00510017 00000303 2F2C000F 00000000"
         "dateTime": "xxx",
- Time the log was created
- busctl get-property xyz.openbmc_project.Logging /xyz/openbmc_project/logging/entry/968  xyz.openbmc_project.Logging.Entry Timestamp
- t 1659116081717
         "callout": {
- Information contained in error log
            "priority": "xxx",
- Severity of log
- busctl get-property xyz.openbmc_project.Logging /xyz/openbmc_project/logging/entry/968  xyz.openbmc_project.Logging.Entry Severity
- s "xyz.openbmc_project.Logging.Entry.Level.Warning"
            "locationCode": "xxx",
- Location code, found either in Logging resolution string or as a prop in inventory manager
- busctl get-property xyz.openbmc_project.Logging /xyz/openbmc_project/logging/entry/968  xyz.openbmc_project.Logging.Entry Resolution
            "ccin": "xxx",
- ccin, found either in Logging resolution string or as a prop in inventory manager(need to doublecheck)
- busctl get-property xyz.openbmc_project.Logging /xyz/openbmc_project/logging/entry/968  xyz.openbmc_project.Logging.Entry Resolution
            "serialNumber": "xxx",
- serial number, found either in Logging resolution string or as a prop in inventory manager(need to doublecheck)
- busctl get-property xyz.openbmc_project.Logging /xyz/openbmc_project/logging/entry/968  xyz.openbmc_project.Logging.Entry Resolution
            "partNumber": "xxx"
- part number, found either in Logging resolution string or as a prop in inventory manager(need to doublecheck)
- busctl get-property xyz.openbmc_project.Logging /xyz/openbmc_project/logging/entry/968  xyz.openbmc_project.Logging.Entry Resolution
         },
         "resourceActions": {
            "type": "xxx",
- Type of device the log is associate with
- tail of object associated with log /xyz/openbmc_project/inventory/system/chassis/motherboard/dimm0
            "reasonDescription": "xxx",
- MANUAL / PREDICTIVE / ASSOCIATION values valid
- busctl get-property org.open_power.HardwareIsolation /xyz/openbmc_project/hardware_isolation/events/hw_isolation_status/1 xyz.openbmc_project.Logging.Event Message
- s "Manual"
            "gardRecord": "xxx"
- Is the device guarded?
- busctl get-property xyz.openbmc_project.Inventory.Manager    /xyz/openbmc_project/inventory/system/chassis/motherboard/dimm0 xyz.openbmc_project.Object.Enable Enabled
- b false
         }
      }
   },
   "failInPlace": {
- Believe these are failures that can't be guarded or deconfigured, such as power supplies (and maybe fans?)
      "cec_error_log": "xxx"
   },
   "manualGard": {
      "type": "xxx",
"physicalPath": "xxx",
- Should we include physical path?
      "locationCode": "xxx",
      "pelid": "xxx",
- No pel is created under manual guard, so field not required?
      "currentState": "xxx",
      "reasonDescription": "xxx"
   },
   "deconfigured": {
      "type": "xxx",
- Type of device the deconfiguaration is associate with
     "physicalPath": "physical:sys-0/node-0/proc-0",
- Physical path of the device
      "locationCode": "xxx",
"physicalPath": "physical:sys-0/node-0/proc-0",
      "pelid": "xxx",
- Associate pel log id with hardware deconfiguation if available
      "currentState": "DECONFIGURED",
      "reasonDescription": "NO CHILD DIMM"
   },
   "policy": {
- Not sure where to fetch these values at the moment
      "fco_value": "xxx",
      "master": "xxx",
      "predictive": "xxx"
   }
}


