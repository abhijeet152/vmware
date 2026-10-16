If you're using VMware Workstation on Ubuntu, you can power on a VM from the terminal using the vmrun command.

## 1. Find vmrun

- Check whether it's installed:
    ```
    which vmrun
    ```

  - Common locations:
    ```
    /usr/bin/vmrun
    ```

  - or
    ```
    /usr/lib/vmware/bin/vmrun
    ```

## 2. Locate the VMX file

- Every VMware VM has a .vmx file.

  - For example:
    ```
    /home/user/VMs/UbuntuServer/UbuntuServer.vmx
    ```

  - You can find them with:
    ```
    find ~ -name "*.vmx"
    ```

## 3. Start the VM
    ```
    vmrun start "/home/user/VMs/UbuntuServer/UbuntuServer.vmx"
    ```

- To start it headless (without opening the VMware GUI):
    ```
    vmrun start "/home/user/VMs/UbuntuServer/UbuntuServer.vmx" nogui
    ```

## 4. Check running VMs
    ```
    vmrun list
    ```

  - Example output:
    ```
    Total running VMs: 1
    /home/user/VMs/UbuntuServer/UbuntuServer.vmx
    ```

## 5. Stop the VM

- Graceful shutdown:
    ```
    vmrun stop "/home/user/VMs/UbuntuServer/UbuntuServer.vmx" soft
    ```

- Force power off:
    ```
    vmrun stop "/home/user/VMs/UbuntuServer/UbuntuServer.vmx" hard
    ```

## 6. If vmrun is not available

- Some newer VMware installations do not put it in your PATH. Locate it:
    ```
    find /usr -name vmrun 2>/dev/null
    ```

- Then run it directly:
    ```
    /usr/lib/vmware/bin/vmrun start "/path/to/vm.vmx" nogui
    ```

- Alternative using vmware command

  - If you only need to open the VM in Workstation:
    ```
    vmware "/home/user/VMs/UbuntuServer/UbuntuServer.vmx"
    ```

## Note:
- vmrun is the preferred method for remote SSH administration because it doesn't require interacting with the GUI.
