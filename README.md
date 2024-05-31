In this step-by-step tutorial, you'll learn how to craft effective prompts for ChatGPT using Meraki APIs. Whether you're new to Meraki APIs or looking to enhance your prompt-writing skills, this guide will walk you through the essentials. By the end, you'll be able to create powerful, precise, and functional prompts that leverage the capabilities of Meraki APIs to their fullest potential.

**Step 1: Define the Base Prompt**

The first step in creating an effective ChatGPT prompt using Meraki APIs is to define the base prompt. This involves setting basic parameters and clearly specifying your requirements. A well-defined base prompt ensures that ChatGPT understands the task and delivers precise, actionable responses.

**Example Base Prompt:**

```
Create Meraki APIv1 script using Python. Do not exceed more than 10 calls per second. Use the Python requests library and do not use any libraries that are not standard. Run the script on a loop every 5 seconds.
```

**__________________________________________________________________________________**

**Step 2: API Call**

Once you have your base prompt defined, the next step is to identify the correct Meraki API call that your script needs to execute. Visit the [Meraki API documentation](https://developer.cisco.com/meraki/api-v1/) to find the appropriate API endpoints and understand their parameters.


**Example API Call:**

```
First API call to run is as follow POST/organizations/{organizationId}/networks
```


**__________________________________________________________________________________**

**Step 3: API Request Data In**

The next step is to simply copy and paste the request parameters for the chosen API call identified in the previous step. You can find the necessary request parameters on the [Meraki API documentation website](https://developer.cisco.com/meraki/api-v1/).

By copying the request parameters, you ensure that your API calls are properly formatted and include all required information, making your script more robust and functional.

Source: https://developer.cisco.com/meraki/api-v1/create-organization-network/

Once scroll down click request parameters schema definition and click the plus sign to expand
![Request parameters](https://github.com/AlekZurawek/Meraki_Prompt_Engineering/blob/main/images/request_parameters.png?raw=true)

**Example:**

```
Object

copyFromNetworkId: string  
The ID of the network to copy configuration from. Other provided parameters will override the copied configuration, except type which must match this network's type exactly.

name*: string  
The name of the new network

notes: string  
Add any notes or additional information about this network here.

timeZone: string  
The timezone of the network. For a list of allowed timezones, please see the 'TZ' column in the table in this article.

productTypes*: array[]  
The product type(s) of the new network. If more than one type is included, the network will be a combined network.

tags: array[]  
A list of tags to be applied to the network.
```

**__________________________________________________________________________________**


**Step 4: How to obtain data for the required parameters**

Once you have identified the correct API call and copied the necessary request parameters, the next step is to gather the required data for these parameters. Knowing where to source this data is essential for the accurate execution of your API requests.

**Example:**

```
Obtain the “name” parameter from network_names.csv file column 1, row 2 onward, “network_names.csv ” file currently has the following structure: “network_names,network_id
001-Alek Zurawek,”

For productTypes*: array variable always set it to “appliance”. Do not sent any other parameters in the payload!
```

**__________________________________________________________________________________**

**Step 5: Response Data Out**

The next step is to understand what the script should expect as a response from the API call. This involves copying and pasting the expected successful response schema. Knowing the response structure helps you handle the data returned by the API effectively.

Source: https://developer.cisco.com/meraki/api-v1/create-organization-network/

Once scroll down click response parameters schema definition and click the plus sign to expand
![Request parameters](https://github.com/AlekZurawek/Meraki_Prompt_Engineering/blob/main/images/response_parameters.png?raw=true)

**Example:**

```
Object

enrollmentString: string
  Enrollment string for the network

id: string
  Network ID

name: string
  Network name

notes: string
  Notes for the network

organizationId: string
  Organization ID

timeZone: string
  Timezone of the network

url: string
  URL to the network Dashboard UI

isBoundToConfigTemplate: boolean
  If the network is bound to a config template

productTypes: array[]
  List of the product types that the network supports

tags: array[]
  Network tags
```

**__________________________________________________________________________________**

**Step 6: Output Instructions**

The final step is to decide how to handle the response data from the API call. This involves defining what your script should do with the returned data to ensure it is used effectively and meets your needs.

**Example:**

```
Save response data “id” to corresponding “network_names” value in 2nd column called “network_id”
row 2 onwards by editing the “network_names.csv” file do not edit any other fields. Do not create
new networks using the API call that already have a networkId in the network_names.csv file.
Print an indication message that the script is running and if new networks are created print
that in console too.
```

**Final full prompt:**
```
Create Meraki APIv1 script using Python. Do not exceed more than 10 calls per second. Use the Python requests library and do not use any libraries that are not standard. Run the script on a loop every 5 seconds.

First API call to run is as follow POST/organizations/{organizationId}/networks

Object

copyFromNetworkId: string  
The ID of the network to copy configuration from. Other provided parameters will override the copied configuration, except type which must match this network's type exactly.

name*: string  
The name of the new network

notes: string  
Add any notes or additional information about this network here.

timeZone: string  
The timezone of the network. For a list of allowed timezones, please see the 'TZ' column in the table in this article.

productTypes*: array[]  
The product type(s) of the new network. If more than one type is included, the network will be a combined network.

tags: array[]  
A list of tags to be applied to the network.

Obtain the “name” parameter from network_names.csv file column 1, row 2 onward, “network_names.csv ” file currently has the following structure: “network_names,network_id
001-Alek Zurawek,”

For productTypes*: array variable always set it to “appliance”. Do not sent any other parameters in the payload!

Object

enrollmentString: string
  Enrollment string for the network

id: string
  Network ID

name: string
  Network name

notes: string
  Notes for the network

organizationId: string
  Organization ID

timeZone: string
  Timezone of the network

url: string
  URL to the network Dashboard UI

isBoundToConfigTemplate: boolean
  If the network is bound to a config template

productTypes: array[]
  List of the product types that the network supports

tags: array[]
  Network tags

Save response data “id” to corresponding “network_names” value in 2nd column called “network_id”
row 2 onwards by editing the “network_names.csv” file do not edit any other fields. Do not create
new networks using the API call that already have a networkId in the network_names.csv file.
Print an indication message that the script is running and if new networks are created print
that in console too.
```
