# STANDARD-ACL-CONF-ON-ROUTER
Standard ACL configuaration
To configure a standard numbered ACL (Access Control List) to restrict the device with IP address `192.168.1.1` from accessing the server with IP address `192.168.3.1`, follow these steps:

### Configuration Steps:

1. **Access the CLI of the Router** where the ACL will be applied (Router3 in your case).
2. **Create the Standard ACL** to deny access from the specified IP.
3. **Apply the ACL** to the appropriate interface.

### Step-by-Step Commands:

#### Step 1: Create the Standard ACL
```bash
Router(config)# access-list 1 deny 192.168.1.1
Router(config)# access-list 1 permit any
```

#### Step 2: Apply the ACL to the Interface
Assuming you want to apply this ACL on the `GigabitEthernet0/0` interface in the inbound direction:
```bash
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip access-group 1 in
Router(config-if)# exit
```

### Full Configuration Example:

1. **Access Router CLI:**
   ```bash
   enable
   configure terminal
   ```

2. **Create the ACL:**
   ```bash
   access-list 1 deny 192.168.1.1
   access-list 1 permit any
   ```

3. **Apply the ACL to the Interface:**
   ```bash
   interface GigabitEthernet0/0
   ip access-group 1 in
   ```

### Verifying the Configuration

You can verify the ACL configuration by using the following commands:

```bash
show access-lists
show ip interface GigabitEthernet0/0
```

This will display the access list and its application on the interface, ensuring that the device with IP `192.168.1.1` is restricted from accessing the `192.168.3.1` server.

