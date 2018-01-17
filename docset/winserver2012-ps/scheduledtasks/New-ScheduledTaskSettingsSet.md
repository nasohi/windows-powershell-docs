---
external help file: ScheduledTask_Cmdlets.xml
online version: 
schema: 2.0.0
ms.assetid: FBC4B2C5-A56C-4D97-B1AC-20C0A62F8D07
---

# New-ScheduledTaskSettingsSet

## SYNOPSIS
Creates a new scheduled task settings object.

## SYNTAX

```
New-ScheduledTaskSettingsSet [-AllowStartIfOnBatteries] [-AsJob] [-CimSession <CimSession[]>]
 [-Compatibility <CompatibilityEnum>] [-DeleteExpiredTaskAfter <TimeSpan>] [-Disable] [-DisallowDemandStart]
 [-DisallowHardTerminate] [-DisallowStartOnRemoteAppSession] [-DontStopIfGoingOnBatteries] [-DontStopOnIdleEnd]
 [-ExecutionTimeLimit <TimeSpan>] [-Hidden] [-IdleDuration <TimeSpan>] [-IdleWaitTimeout <TimeSpan>]
 [-MaintenanceDeadline <TimeSpan>] [-MaintenanceExclusive] [-MaintenancePeriod <TimeSpan>]
 [-MultipleInstances <MultipleInstancesEnum>] [-NetworkId <String>] [-NetworkName <String>] [-Priority <Int32>]
 [-RestartCount <Int32>] [-RestartInterval <TimeSpan>] [-RestartOnIdle] [-RunOnlyIfIdle]
 [-RunOnlyIfNetworkAvailable] [-StartWhenAvailable] [-ThrottleLimit <Int32>] [-WakeToRun]
```

## DESCRIPTION
The **New-ScheduledTaskSettingsSet** cmdlet creates an object that contains scheduled task settings.
Each scheduled task has one set of task settings.
Use this cmdlet to configure options to manage the behavior of the task upon completion, to manage the behavior of the task if a problem occurs, or to manage the behavior of the task if an instance of the task is already running.

You can use the scheduled task settings to register a new scheduled task or update an existing task registration.

## EXAMPLES

### Example 1: Register a scheduled task that uses default task settings
```
The first command creates a scheduled task action named Cmd and assigns the **ScheduledTaskAction** object to the Sta variable.
PS C:\>$Sta = New-ScheduledTaskAction -Execute "Cmd"

The second command creates scheduled task settings that use the default settings and assigns the **ScheduledTaskSettings** object to the Stset variable.
PS C:\>$STSet = New-ScheduledTaskSettingsSet

The third command registers the scheduled task Task01 to run the task action named Cmd and to use the default task settings.
PS C:\>Register-ScheduledTask Task01 -Action $Sta -Settings $STSet
```

This example registers a scheduled task that uses default task settings.

### Example 2: Set the priority of a scheduled task
```
The first command creates a scheduled task action named Cmd and assigns the **ScheduledTaskAction** object to the Sta variable.
PS C:\>$Sta = New-ScheduledTaskAction -Execute "Cmd"

The second command creates scheduled task settings that sets a higher priority for the scheduled task, and assigns the **ScheduledTaskSettings** object to the Stset variable.
PS C:\>$STSet = New-ScheduledTaskSettingsSet -Priority 5

The third command registers the scheduled task Task01 to run the task action named Cmd and to use the task settings that have a priority setting of 9.
PS C:\>Register-ScheduledTask Task01 -Action $Sta -Settings $Stset
```

This example sets the priority of a scheduled task.

### Example 3: Set restart settings for a scheduled task
```
The first command creates a scheduled task action named Cmd and assigns the **ScheduledTaskAction** object to the Sta variable.
PS C:\>$Sta = New-ScheduledTaskAction -Execute "Cmd"

The second command creates scheduled task settings that specify that Task Scheduler attempts three restarts of the task at sixty minute intervals. This command assigns the **ScheduledTaskSettings** object to the Stset variable.
PS C:\>$Stset = New-ScheduledTaskSettingsSet -RestartCount 3 -RestartInterval 60

The third command registers the scheduled task Task01 to run the task action named Cmd and to use the task settings that the **ScheduledTaskSettings** object defines.
PS C:\>Register-ScheduledTask Task01 -Action $Sta -Settings $Stset
```

This example sets restart settings for a scheduled task.

### Example 4: Set idle settings for a scheduled task
```
The first command creates a scheduled task action named Cmd and assigns the **ScheduledTaskAction** object to the Sta variable.
PS C:\>$Sta = New-ScheduledTaskAction -Execute "Cmd"

The second command creates scheduled task settings that specify that Task Scheduler runs the task only when the computer is idle for 2 minutes and waits for 2 hours and 30 minutes for an idle condition. This command assigns the **ScheduledTaskSettings** object to the Stset variable.
PS C:\>$Stset = New-ScheduledTaskSettingsSet -RunOnlyIfIdle -IdleDuration 00:02:00 -IdleWaitTimeout 02:30:00

The third command registers the scheduled task Task01 to run the task action named Cmd and to use the task settings that the **ScheduledTaskSettings** object defines.
PS C:\>Register-ScheduledTask Task01 -Action $Sta -Settings $Stset
```

This example sets idle settings for a scheduled task.

### Example 5: Register a scheduled task that runs only when a network is available
```
The first command creates a scheduled task action named Cmd and assigns the **ScheduledTaskAction** object to the Sta variable.
PS C:\>$Sta = New-ScheduledTaskAction -Execute "Cmd"

The second command creates scheduled task settings that specify that Task Scheduler runs the task only when a network is available. This command assigns the **ScheduledTaskSettings** object to the Stset variable.
PS C:\>$Stset = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable

The third command registers the scheduled task Task01 to run the task action named Cmd only when a network is available.
PS C:\>Register-ScheduledTask Task01 -Action $Sta -Settings $Stset
```

This example registers a scheduled task that runs only when a network is available.

## PARAMETERS

### -AllowStartIfOnBatteries
Indicates that Task Scheduler starts if the computer is running on battery power.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
ps_cimcommon_asjob

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession
Runs the cmdlet in a remote session or on a remote computer.
Enter a computer name or a session object, such as the output of a New-CimSessionhttp://go.microsoft.com/fwlink/p/?LinkId=227967 or Get-CimSessionhttp://go.microsoft.com/fwlink/p/?LinkId=227966 cmdlet.
The default is the current session on the local computer.

```yaml
Type: CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Compatibility
Indicates which version of Task Scheduler with which a task is compatible.
The acceptable values for this parameter are:
- At
- V1
- Vista
- Win7
- Win8

```yaml
Type: CompatibilityEnum
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DeleteExpiredTaskAfter
Specifies the amount of time that Task Scheduler waits before deleting the task after it expires.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Disable
Indicates that the task is disabled.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisallowDemandStart
Indicates that the task cannot be started by using either the Run command or the Context menu.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisallowHardTerminate
Indicates that the task cannot be terminated by using TerminateProcess.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisallowStartOnRemoteAppSession
Indicates that the task does not start if the task is triggered to run in a Remote Applications Integrated Locally (RAIL) session.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DontStopIfGoingOnBatteries
Indicates that the task does not stop if the computer switches to battery power.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DontStopOnIdleEnd
Indicates that Task Scheduler does not terminate the task if the idle condition ends before the task is completed.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExecutionTimeLimit
Specifies the amount of time that Task Scheduler is allowed to complete the task.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Hidden
Indicates that the task is hidden in the Task Scheduler UI.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleDuration
Specifies the amount of time that the computer must be in an idle state before Task Scheduler runs the task.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleWaitTimeout
Specifies the amount of time that Task Scheduler waits for an idle condition to occur.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaintenanceDeadline
Specifies the amount of time after which Task Scheduler attempts to run the task during emergency Automatic maintenance, if the task failed to complete during regular Automatic maintenance.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaintenanceExclusive
Indicates that the task needs to run alone when it is started in maintenance mode.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaintenancePeriod
Specifies the amount of time that the task needs to run once during regular Automatic maintenance.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MultipleInstances
Specifies the policy that defines how Task Scheduler handles multiple instances of the task.

```yaml
Type: MultipleInstancesEnum
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NetworkId
Specifies the ID of a network profile that Task Scheduler uses to determine if the task can run.
You must specify the ID of a network if you specify the **RunOnlyIfNetworkAvailable** paramater.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NetworkName
Specifies the name of a network profile that Task Scheduler uses to determine if the task can run.
The Task Scheduler UI uses this setting for display purposes.
Specify a network name if you specify the **RunOnlyIfNetworkAvailable** paramater.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Priority
Specifies the priority level of the task.
Priority must be an integer from 0 (highest priority) to 10 (lowest priority).
The default value is 7.

Priority levels 7 and 8 are used for background tasks.
Priority levels 4, 5, and 6 are used for interactive tasks.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestartCount
Specifies the number of times that Task Scheduler attempts to restart the task.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestartInterval
Specifies the amount of time that Task Scheduler attempts to restart the task.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestartOnIdle
Indicates that Task Scheduler restarts the task when the computer cycles into an idle condition more than once.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunOnlyIfIdle
Indicates that Task Scheduler runs the task only when the computer is idle.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunOnlyIfNetworkAvailable
Indicates that Task Scheduler runs the task only when a network is available.
Task Scheduler uses the **NetworkID** paramater and **NetworkName** parameter that you specify in this cmdlet to determine if the network is available.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartWhenAvailable
Indicates that Task Scheduler can start the task at any time after its scheduled time has passed.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Specifies the maximum number of concurrent operations that can be established to run the cmdlet.
If this parameter is omitted or a value of `0` is entered, then Windows PowerShell® calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.
The throttle limit applies only to the current cmdlet, not to the session or to the computer.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WakeToRun
Indicates that Task Scheduler wakes the computer before it runs the task.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

## OUTPUTS

### Microsoft.Management.Infrastructure.CimInstance#MSFT_TaskSettings

## NOTES

## RELATED LINKS

[Register-ScheduledTask](./Register-ScheduledTask.md)

[New-ScheduledTask](./New-ScheduledTask.md)

[Get-ScheduledTask](./Get-ScheduledTask.md)

[Get-ScheduledTaskInfo](./Get-ScheduledTaskInfo.md)

[Unregister-ScheduledTask](./Unregister-ScheduledTask.md)

[Enable-ScheduledTask](./Enable-ScheduledTask.md)

[Start-ScheduledTask](./Start-ScheduledTask.md)
