In this step-by-step tutorial, you'll learn how to craft effective prompts for ChatGPT using Meraki APIs. Whether you're new to Meraki APIs or looking to enhance your prompt-writing skills, this guide will walk you through the essentials. By the end, you'll be able to create powerful, precise, and functional prompts that leverage the capabilities of Meraki APIs to their fullest potential.

**Step 1: Define the Base Prompt**

The first step in creating an effective ChatGPT prompt using Meraki APIs is to define the base prompt. This involves setting basic parameters and clearly specifying your requirements. A well-defined base prompt ensures that ChatGPT understands the task and delivers precise, actionable responses.

**Example Base Prompt:**

```
Create Meraki APIv1 script using Python. Do not exceed more than 10 calls per second. Use the Python requests library and do not use any libraries that are not standard. Run the script on a loop every 5 seconds.
```

**Step 2: API Call**

Once you have your base prompt defined, the next step is to identify the correct Meraki API call that your script needs to execute. Visit the [Meraki API documentation](https://developer.cisco.com/meraki/api-v1/) to find the appropriate API endpoints and understand their parameters.


**Example API Call:**

```
First API call to run is as follow POST/organizations/{organizationId}/networks
```

**Step 3: Copy & Paste the Request Parameters**

The next step is to simply copy and paste the request parameters for the chosen API call identified in the previous step. You can find the necessary request parameters on the [Meraki API documentation website](https://developer.cisco.com/meraki/api-v1/).

By copying the request parameters, you ensure that your API calls are properly formatted and include all required information, making your script more robust and functional.

Source: https://developer.cisco.com/meraki/api-v1/create-organization-network/

Once scroll down click request parameters and click the plus sign to expand
![Request parameters](https://github.com/AlekZurawek/Meraki_Prompt_Engineering/blob/main/images/request_parameters.png?raw=true)

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

**Step 4: How to obtain data for the required parameters**

Once you have identified the correct API call and copied the necessary request parameters, the next step is to gather the required data for these parameters. Knowing where to source this data is essential for the accurate execution of your API requests.

**Example:**

```
Obtain the “name” parameter from network_names.csv file column 1, row 2 onward, “network_names.csv ” file currently has the following structure: “network_names,network_id
001-Alek Zurawek,”

For productTypes*: array variable always set it to “appliance”.
```
