# Nag Functionality

Author: Noah Brewer
  < Human3rr, Shantappa Teekappanavar, Matt Spinler, Kanisha Patel >

Created: July 13, 2022
Last Updated: July 19, 2022

## Problem Description

We need a way to monitor and report back to IBM critical hardware issues on 
customers systems.

We already will collect guard records and PEL logs but customers sometimes don't
recognize their systems are in a depreciated state and should address these
issues either by replacing faulty components or by explicitly ignoring failures.

## Background and References

Nag functionality existed for FSP systems starting for the P7 release. There is 
a need to port the functionality over to the BMC to detect and resolve similar 
hardware failures with reminders and periodic checks to confirm issues are 
either resolved or *explicitly* ignored.
 
Solution for customer system unscheduled incident repair action (UIRA) and long
	outage impact due to one of the following reasons:
- Predictive Memory Error become Uncorrectable Error, second System Clock card
	failure
- SSR closing all serviceable events with non-functional hardware left in the 
	system
- Customer delaying or ignoring required service action that can lead to UIRA

## Requirements
### High Level Requirements
- Create XML (or JSON TBD) file which contains hardware failures
    - Must gather BMC deconfig and guarded data
    - Gather PSUs, Fans, and Hotplug devices if any service actions are required
    - Include timestamp of the platform event log (PEL) that triggered the Guarded hardware
    - Include inventory object path 
    - Include deconfig table showing all resources deconfigured by association
    - Include information on each guarded unit:
        - State of unit
        - Location code
        - PHAL Device Tree shared with Hostboot

- Periodically create XML if there are resources guarded or deconfigured under the following events:
    - On power on
    - At end of R&V repair
    - Monthly check
    - During BMC failover
    - Optionally ignore SRC for selectable guarded hardware

- If hardware failures are present, log a Call Home Serviceable Event Log to indicate the condition.

- Export XML to HMC upon request
- Export XML to OS/PLDM on request
   - Provide interface for call for XML file
        - Redfish and D-Bus interface for requests for data from HMC and PLDM

## Proposed Design

TBD

## Alternatives Considered

TBD

## Impacts

TBD

## Testing

TBD
