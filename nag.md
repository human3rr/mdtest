# Nag Functionality

Author: Noah Brewer
  < Human3rr, Shantappa Teekappanavar, Matt Spinler >

Created: July 13, 2022
Last Updated: July 25, 2022

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
    - Include timestamp of the platform event log (PEL) that triggered the 
	guarded hardware
    - Include inventory object path 
    - Include deconfig table showing all resources deconfigured by association
    - Include information on each guarded unit:
        - State of unit
        - Location code
        - PHAL Device Tree shared with Hostboot

- Periodically create XML and raise servicable event if there are resources 
	guarded or deconfigured under the following events:
    - On BMC power on
    - At end of R&V repair
    - A monthly check
        - A periodic "Pending HW Repair Reminder" timer in BMC. The timer will 
	trigger BMC to check the guard record during runtime, if guarded 
	hardware exist, create a new Call Home Serviceable Event with new SRC

    - Optionally ignore creating SRC for selectable guarded hardware
    - During BMC failover (If redundant BMCs are supported in future)

- If hardware failures are present, log a Call Home Serviceable Event Log to 
	indicate the condition by creating PEL with associated system reference code (SRC). 

- The unique SRC description indicating that there are "Defective CEC Hardware 
	in the system pending repair".
    - SRC B150F138 for [P10 systems](https://supportcontent.ibm.com/support/pages/service-action-required-srcs-b175f138-or-b150f138?check_logged_in=1)
    - Extended words should be populated with corresponding data: [Defined](https://supportcontent.ibm.com/support/pages/service-action-required-srcs-b175f138-or-b150f138?check_logged_in=1)

- Export XML to HMC, and OS/PLDM on request
   - Provide interface for call for XML file
        - Redfish and D-Bus interface for requests for data from HMC and PLDM

- Command line interface for display of data on BMC

## Proposed Design

TBD

## Alternatives Considered

TBD

## Impacts

TBD

## Testing

TBD
