# Zabbix Template - DSE7420 MKII SNMP

Zabbix 7.4 template for **Deep Sea Electronics DSE7420 MKII** monitoring over **SNMP v2c**.

This template was built and validated against a real device and includes:

- Generator monitoring
- Engine monitoring
- Basic triggers
- Template dashboard
- Support for nullable/raw SNMP values
- SNMP trap raw item

## Tested environment

- Device: **DSE7420 MKII**
- Firmware: **V7.7.3**
- Zabbix: **7.4**
- SNMP: **v2c**

## Included monitoring items

### System
- System description
- System name
- System uptime

### Engine
- Engine key ID
- Battery voltage
- Engine speed display
- Oil pressure raw
- Coolant temperature raw
- Engine RPM raw
- Warning alarm raw
- Shutdown alarm raw
- Electrical trip raw

### Generator
- Generator key ID
- Frequency
- L1 voltage
- L2 voltage
- L3 voltage
- L1 current
- L2 current
- L3 current
- Total watts
- Total VA
- Total VAr
- Total power factor raw
- Total phase
- Average LN voltage
- Average current

### Trap
- SNMP trap raw item

## Triggers

- No battery voltage data received
- Battery voltage low
- Battery voltage high
- Engine speed high
- Generator frequency high
- Engine running but generator frequency low
- Generator L1/L2/L3 voltage low/high

## Notes

Some DSE OIDs may return `NULL` depending on:

- generator state
- sensor availability
- controller configuration
- firmware behavior

Because of that, some items are intentionally kept as `raw` character items instead of numeric items.

## Import

1. Go to:
   - `Data collection -> Templates -> Import`
2. Import the YAML file
3. Link the template to your host
4. Set host SNMP interface
5. Set macro:

```text
{$SNMP_COMMUNITY}=your_community
