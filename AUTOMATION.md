# Automating a Range of Operations Based on a Template

To automate a range of operations using a provided template, follow these steps:

1. **Download the Template**: Obtain the template file from [this link](https://github.com/hellzerg/optimizer/blob/master/templates/optimizer-template.json).

2. **Edit the Template**: Customize the template configuration according to your needs.

3. **Execute the Optimizer**: Run the optimizer executable with the edited template configuration using the command: `optimizer.exe /config=template.json`

## Template Configuration Options

### WindowsVersion (required)
- Should match your actual Windows version. Available values: `7 | 8 | 10 | 11`

### Cleaner
- Choose target folders for cleaning by marking them as `true`.

### Pinger
- Choose DNS provider:
- Available values: `Automatic | Cloudflare | OpenDNS | Quad9 | Google | AlternateDNS | Adguard | CleanBrowsing | CleanBrowsing (adult filter)`
- Set FlushDNSCache to `true` to perform DNS cache flushing. Example:

 ```
 "Pinger": {
     "SetDNS": "Cloudflare",
     "FlushDNSCache": true
 }
 ```

### ProcessControl
- Prevent processes from running by providing filenames.
- Allow previously prevented processes to run again. Example:

 ```
 "ProcessControl": {
     "Prevent": ["chrome.exe", "firefox.exe"],
     "Allow": ["opera.exe"]
 }
 ```

### Hosts
- Manage hosts entries:
- Entries in the `Block` list route to `0.0.0.0`, effectively blocking access.
- Entries in the `Add` list are added. Example:

 ```
 "HostsEditor": {
     "Block": ["youtube.com", "google.com"],
     "Add": [
         {
             "Domain": "test.com",
             "IPAddress": "192.168.1.5",
             "Comment": "comment is optional"
         },
         {
             "Domain": "test2.com",
             "IPAddress": "192.168.1.9",
             "Comment": ""
         }
     ]
 }
 ```

### RegistryFix
- Enable core Windows components by marking them as `true`. Use for repairing computers from malicious actions.

### Integrator
- `TakeOwnership`: Add or remove "Take Ownership" option in right-click menu. (`false`)
- `OpenWithCMD`: Add or remove "Open CMD here" option in right-click menu. (`false`)

### AdvancedTweaks
- Caution: These tweaks are technical, avoid unless you understand them.
- `UnlockAllCores`: Leave `null` or `false`.
- `DisableHPET`: Enable or disable High Precision Event Timer.
- `EnableLoginVerbose`: Enable or disable Detailed Login Screen.

#### SvchostProcessSplitting
- Mark `true` to reduce svchost.exe processes for optimal memory.
- Mark `false` to enable process splitting for optimal performance.

### Tweaks
- Mark options to apply as `true`.
- Mark options to reset as `false`.
- Mark options to ignore as `null`.

### PostAction
- Final action after template execution:
- Mark `Restart` as `true` to restart and apply changes.
- Configure `RestartType` for different restart types (`Normal` or `SafeMode`).
- Use `DisableDefender` and `EnableDefender` for automated Windows Defender control.

**Note**: Review and customize the template configuration carefully before executing.