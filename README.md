# XIQ - Add PPSK users from a CSV file
## XIQ_PPSK_CSV_Importer.py
### Purpose
This script will import a CSV file of PPSK Users and remove these users on the entered the user group.

## User Input Data
##### lines 27-28
```
#XIQ_username = "enter your ExtremeCloudIQ Username"
#XIQ_password = "enter your ExtremeCLoudIQ password"
```
or 
##### line 31
```
XIQ_token = "****"
```
A token can be generated using the POST /auth/apitoken with both the "enduser",“pcg:key” permissions set in the body. This can be done from the [Swagger page](https://api.extremecloudiq.com/swagger-ui/index.html?configUrl=/openapi/swagger-config&layout=BaseLayout#/Authorization/generateApiToken).

##### line 35-36
```
group_roles = {
    # User Group Name, XIQ group ID
    "User Group Name 1": "XIQ group 1 ID",
    "User Group Name 2": "XIQ group 2 ID"
}
```
Each XIQ User Group will be assigned a unique ID when it gets created. This is something that gets used by the backend systems and not seen in the GUI. The easiest way to get the ID is from the [Swagger page](https://api.extremecloudiq.com/swagger-ui/index.html?configUrl=/openapi/swagger-config&layout=BaseLayout#/Configuration%20-%20User%20Management/listUserGroups). 

### Optional
##### line 21
```
filename = "PPSK_Users.csv"
```
The file name can be changed if needed.

##### line 39
```
PCG_Enable = False
```
set to True if PCG will be used. Then update the PCG_Mapping
```
PCG_Mapping = {
    "XIQ User Group ID" : {
        "UserGroupName": "XIQ User Group Name",
        "policy_id": "Network Policy ID associated with PCG",
         "policy_name": "Network Policy name associated with PCG"
    }
}
```

## Log file
upon running the script a XIQ_PPSK_CSV_Remover.log file will be create. This will be a log file of all users deleted from the user group.

## Requirements
The following modules will need to be installed in order for the script to run.
```
requests
pandas
```