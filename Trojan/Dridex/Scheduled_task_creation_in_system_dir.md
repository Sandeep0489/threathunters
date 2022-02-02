# Dridex

Use this query to look for Dridex persistence behavior.

## Query

### Scheduled task creation containing system directory

```
type_id:8001 and event_actor.file.name:cmd.exe and process.file.name:schtasks.exe and (process.cmd_line:"*schtasks.exe /Create /F /TN*" and (process.cmd_line:"*/TR C:\Windows\System32\*" or process.cmd_line:"*/TR C:\Windows\SysWOW64\*" or 
process.cmd_line:"*/TR CSIDL_SYSTEM\*" or process.cmd_line:"*/TR CSIDL_SYSTEMX86\*")) and (-process.file.normalized_path:CSIDL_SYSTEM\* and -process.file.normalized_path:CSIDL_SYSTEMX86\*)

```