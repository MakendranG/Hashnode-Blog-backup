## How to run scripts in your virtual machine with the Run command

Scripts can be embedded in  properties or referenced to pre-released library scripts. The original command set was action-oriented. The updated command set, currently in public preview, is management-oriented and allows you to run multiple scripts with fewer restrictions. This article explains the difference between the two sets of run commands and helps you decide which  is the right one to use in your scenario.  

**When to use an action or managed commands **


The initial set of commands is action-oriented. You should consider using this set of commands in situations where it needs to be run: 

1. A small script to get stuff from a virtual machine 
2. A script to configure a virtual machine 
3. A single script for diagnostics



# Action Commands


## Run scripts in your Linux virtual machine using the Run Commands action 

The Run Command feature uses a virtual machine agent to run `shell scripts` in an Azure Linux virtual machine. You can use these scripts for general machine or application management. They can help you  quickly diagnose and resolve virtual machine access and network problems, and restore virtual machines to a good state. 

### Advantages

- You can access your virtual machine in a number of ways. 
- Run Command can run scripts on your virtual machine remotely  using  VM Agent. 
- You use the Run command over the **Azure portal, REST API, or Azure CLI** for Linux virtual machines. 
- This feature is useful in all situations where you want to run a script in a virtual machine. 
- This is one of the only ways to `troubleshoot and fix virtual machines whose RDP or SSH ports are not open` due to network configuration or administrative users.

### Available commands 

#### Azure CLI 

The following example uses the `az vm run-command` command to run a shell script on an Azure Linux virtual machine.

```
az vm run-command invoke -g demoRG -n demoVM --command-id RunShellScript --scripts "apt-get update && apt-get install -y nginx"
```


#### Azure Portal

Navigate to a virtual machine in the Azure portal and select `Run command` from the left menu under Activities. You will see a list of commands available  to run on the virtual machine. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659034290184/2atykEg0Q.png align="left")


Select a command to run. Some  commands may have optional or required input parameters. For these commands, the parameters are presented as text fields for you to provide  input values. For each command, you can see the script  being executed by expanding Viewscript. 

**RunShellScript** is different from  other commands because it allows you to provide your own custom script.  After selecting the command, select Run to run the script. When the script completes, it returns the output and any errors to the output window. The following screenshot shows sample results from running the `ifconfig` command. 
 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659034330800/HkR236IR2.png align="left")

#### PowerShell 

The following example uses the `Invoke-AzVMRunCommand` cmdlet to run a PowerShell script on an Azure virtual machine. The cmdlet expects the script referenced in the -ScriptPath parameter to be local to where the cmdlet is executed. 

```
Invoke-AzVMRunCommand -ResourceGroupName 'demoRG' -Name 'demoVM' -CommandId 'RunShellScript' -ScriptPath '<pathToScript>' -Parameter @{"arg1" = "var1";"arg2" = "var2"}
```


## Run scripts in your Windows virtual machine using the Run Commands action 

The Run Command feature uses a virtual machine agent (VM)  to run `PowerShell scripts` in a Windows Azure virtual machine. You can use these scripts for general machine or application management. They can help you  quickly diagnose and resolve virtual machine access and network problems, and restore virtual machines to a good state. 

### Advantages

You can access your virtual machine in a number of ways. Run Command can run scripts on your virtual machine remotely  using  VM Agent. You use Run Command over the Azure portal, REST API, or PowerShell for Windows virtual machines. 

This feature is useful in all situations where you want to run a script in a virtual machine. This is one of the only ways to `troubleshoot and repair virtual machines whose RDP or SSH ports are not open` due to network or admin user misconfiguration. 

### Available commands 

#### Azure CLI 

The following example uses the `az vm run-command` command to run a shell script on a Windows Azure virtual machine. 

```
# script.ps1
#   param(
#       [string]$arg1,
#       [string]$arg2
#   )
#   Write-Host This is a sample script with parameters $arg1 and $arg2

az vm run-command invoke  --command-id RunPowerShellScript --name demowinvm -g demoRG \
    --scripts @script.ps1 --parameters "arg1=somefoo" "arg2=somebar"
```

#### Azure Portal

Navigate to a virtual machine in the Azure portal and select Run command from the left menu under Activities. You will see a list of commands available  to run on the virtual machine. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659034580393/7-fE1HSfK.png align="left")

Select a command to run. Some  commands may have optional or required input parameters. For these commands, the parameters are presented as text fields for you to provide  input values. For each command, you can see the script  being executed by expanding Viewscript. 

**RunPowerShellScript** is different from  other commands because it allows you to provide your own custom script.  After selecting the command, select Run to run the script. When the script completes, it returns the output and any errors to the output window. The following screenshot shows sample results from running the `RDPSettings` command.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659034616388/Poqr2BJyl.png align="left")

#### PowerShell 

The following example uses the `Invoke-AzVMRunCommand` cmdlet to run a PowerShell script on an Azure virtual machine. The cmdlet expects the script referenced in the -ScriptPath parameter to be local to where the cmdlet is executed.

```
Invoke-AzVMRunCommand -ResourceGroupName 'demoRG' -Name 'demowinvm' -CommandId 'RunPowerShellScript' -ScriptPath '<pathToScript>' -Parameter @{"arg1" = "var1";"arg2" = "var2"}
```
# Managed Commands


The updated command set, currently in public preview, is management-oriented. Consider using managed run commands if your needs fit the following examples: 

- Scripts must run as part of the VM deployment. 
- Periodic script execution is required.
- Multiple scripts must be executed sequentially. 
- Start the virtual machine by running the installation scripts. 
- Publish a custom script to share and reuse.

 
## Run scripts in your Linux virtual machine using managed run commands 


The update-managed run command uses the same VM agent channel to run scripts and provides the following improvements over the original action-driven run command: 

1. runtime is updated  through the deployment model deploy ARM  
2. Parallel execution of multiple scripts 
3. Sequential execution of scripts 
4. RunCommand script can be canceled 
5. User-specified script timeout 
6. Supports long running scripts (hours/days)  
7. Pass secrets (parameters, passwords) securely 

### Sign up to preview 

You must register your subscription  to use Managed Run Command during public preview. Go to configuring preview features in Azure subscriptions for  instructions on registering and using the `RunCommandPreview` feature name. 

### Available commands 


#### Azure CLI 

The following examples use the run `az vm command` to run shell scripts on an Azure Linux virtual machine. 

**Executing a script with  VM** 

This command will feed the script to the virtual machine, run it and return the captured output.  

```
az vm run-command create --name "demoRunCommand" --vm-name "demoVM" --resource-group "demoRG" --script "echo Welcome to Cloud!"
```

**List all the RunCommand resources deployed in a virtual machine** 

This command will return a complete list of previously deployed commands along with their properties. 


```
az vm run-command list --vm-name "demoVM" --resource-group "demoRG"
```
**Get execution status and results** 

This command retrieves the progress of the current running process, including the last exit, start/end time, exit code, and terminal status of the run. 

```
az vm run-command show --name "demoRunCommand" --vm-name "demoVM" --resource-group "demoRG" --expand instanceView
```

**Remove RunCommand resources from  VM** 

Remove the RunCommand resource that was previously deployed to the VM. If  script execution is still in progress, execution will be interrupted. 

```
az vm run-command delete --name "demoRunCommand" --vm-name "demoVM" --resource-group "demoRG"
```


#### PowerShell 

**Run a script with  VM **

This command will feed the script to the virtual machine, run it and return the captured output.  

```
Set-AzVMRunCommand -ResourceGroupName "demoRG" -VMName "demoVM" -Location "WestUS" -RunCommandName "RunCommandName" –SourceScript "echo Welcome to Cloud!"
```

**List all the RunCommand resources deployed in a virtual machine** 

This command will return a complete list of previously deployed commands along with their properties. 

```
Get-AzVMRunCommand -ResourceGroupName "demoRG" -VMName "demoVM"
```

**Get execution status and results** 

This command retrieves the progress of the current running process, including the last exit, start/end time, exit code, and terminal status of the run. 

```
Get-AzVMRunCommand -ResourceGroupName "demoRG" -VMName "demoVM" -RunCommandName "RunCommandName" -Expand instanceView
```


**Remove RunCommand resources from  VM** 

Remove the RunCommand resource that was previously deployed to the VM. If  script execution is still in progress, execution will be interrupted. 

```
Remove-AzVMRunCommand -ResourceGroupName "demoRG" -VMName "demoVM" -RunCommandName "RunCommandName"
```


## Run scripts in your Windows virtual machine using managed run commands 


Updated managed run command uses the same VM agent channel to run scripts and provides the following improvements over the original action-driven run command:

1. Support for executing updated commands via ARM deployment templates 
2. Parallel execution of multiple scripts 
3. Sequential execution of scripts 
4. RunCommand script can be aborted 
5. User-specified script timeout 
6. Support for long-running (hours / day) scripts 
7. Disclose secrets (parameters, passwords) in a secure manner

### Sign up to preview 

You must register for a subscription  to use Managed Run Command during public preview. For registration instructions, go to Set up the preview feature on your Azure subscription  and use the feature name `RunCommandPreview`. 

### Available commands 

#### Azure CLI 

The following example uses az vm run-command to run a shell script on an Azure Windows VM. 

**Run the script on the VM**

This command sends the script to the VM for execution and returns the captured output. 

```
az vm run-command create --name "demoRunCommand" --vm-name "demoVM" --resource-group "demoRG" --script "echo Welcome to Cloud!"
```


**Lists all RunCommand resources deployed on the VM**

This command returns a complete list of previously provided execution commands and their properties.  

```
az vm run-command list --vm-name "demoVM" --resource-group "demoRG"
```

**Get execution status and results** 

This command gets the current execution progress, such as last output, start / end time, end code, and exit status of the execution. 


```
az vm run-command show --name "demoRunCommand" --vm-name "demoVM" --resource-group "demoRG" --expand instanceView
```

**Remove the RunCommand resource from the VM** 

Delete the RunCommand resource that was previously deployed on the VM. If the script  is still running, it will stop running. 

```
az vm run-command delete --name "demoRunCommand" --vm-name "demoVM" --resource-group "demoRG"
```

#### Powershell 

**Run the script in  the VM** 

This command sends the script to the VM for execution and returns the captured output. 

```
Set-AzVMRunCommand -ResourceGroupName "demoRG" -VMName "demoVM" -Location "WestUS" -RunCommandName "RunCommandName" –SourceScript "echo Welcome to Cloud!"
```

**Lists all  RunCommand resources deployed on the VM** 

This command returns a complete list of previously provided execution commands and their properties. 

```
Get-AzVMRunCommand -ResourceGroupName "demoRG" -VMName "demoVM"
```

**Get execution status and results** 

This command gets the current execution progress, such as last output, start / end time, end code, and exit status of the execution. 

```
Get-AzVMRunCommand -ResourceGroupName "demoRG" -VMName "demoVM" -RunCommandName "RunCommandName" -Expand instanceView
```

**Remove the RunCommand resource from the VM** 


Delete the RunCommand resource that was previously deployed on the VM. If the script  is still running, it will stop running.

```
Remove-AzVMRunCommand -ResourceGroupName "demoRG" -VMName "demoVM" -RunCommandName "RunCommandName"
```


Gratitude for perusing my article till end. I hope you realized something unique today. If you enjoyed this article then please share to your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)