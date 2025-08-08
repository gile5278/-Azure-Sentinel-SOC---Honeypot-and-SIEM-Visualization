# Active Directory Attack Lab – Setup

## Prerequisites
Make sure you have:
- An active Azure subscription
- Appropriate permissions to create resources (Resource Group, VNet, VM, etc.)
- [Optional] A Windows client VM for conducting attacks


---

## 1. Create a Resource Group
1. Go to Azure Portal → **Create a resource group**
2. Fill in the **Name** and **Region**, then click **Review + create** → **Create**
   
	![Resource Group Screenshot](../Document_Images/image15.png)

---

## 2. Configure Network and VM
1. **Create a Virtual Network (VNet)** within your resource group 

   ![Create VNet](../Document_Images/image3.png)

2. **Deploy a VM (Honeypot)**  
   - Use a Windows Server image  
   - Set the password to a known test value (e.g., `Cyberlab123!`) 
   
   ![Deploy VM](../Document_Images/image13.png)

---

## 3. Adjust Firewall Rules
1. Navigate to the VM's **Network Security Group**  
2. **Remove** default RDP rule (if needed)  
3. **Add** inbound rule to allow attack vectors (e.g., RDP for testing) 

    ![Resource Group Screenshot](../Document_Images/image19A.png)

    ![Configure Firewall](../Document_Images/image6.png)

---

## 4. Access the VM
1. Copy the VM’s **Public IP**  
2. Use Remote Desktop (RDP) to connect with `/username` and `/password`

    ![Remote Desktop Login](../Document_Images/image1.png)

3. On success, you'll land on the VM desktop

    ![Login Successful](../Document_Images/image2.png)

---

## 5. Disable Windows Firewall 
1. From the VM:```powershell```wf.msc
Go to Windows Defender Firewall settings and turn off firewall for all profiles (Domain, Private, Public)
	![Resource Group Screenshot](../Document_Images/image21.png)

2. On your local machine, open **Command Prompt** (`cmd`) and run a `ping` command to the VM's public IP to verify network connectivity.

     ![Resource Group Screenshot](../Document_Images/image5.png)

---

## 6. Create Log Analytics Workspace
1. In the Azure Portal → Create a Log Analytics Workspace

     ![Resource Group Screenshot](../Document_Images/image4.png)

---

## 7. Enable Microsoft Sentinel & Content Hub
1. Go to Microsoft Sentinel → Add your new workspace (`LOG-SOC-LAB1`)

    ![Resource Group Screenshot](../Document_Images/image8.png)

2. Use Content Hub to search for and install "Windows Security Events via AMA"

    ![Resource Group Screenshot](../Document_Images/image17A.png)

3. Navigate to its Connector page

    ![Resource Group Screenshot](../Document_Images/image14.png)

4. Set up a Data Collection Rule (DCR) for log ingestion

    ![Resource Group Screenshot](../Document_Images/image9.png)

---

## 8. Upload GeoIP Watchlist
Use this to enrich SSH/attack logs with geolocation:

1. Create a watchlist in Sentinel using your geoip-summarized.csv

	![Resource Group Screenshot](../Document_Images/image16.png)

3. Upload relevant columns: IP, latitude, longitude, city, country

    ![Resource Group Screenshot](../Document_Images/image12.png)
   
3. After finished upload, you are able to see 1 watchlists and 55k watchlist items.

     ![Resource Group Screenshot](../Document_Images/image11.png)

---

## 9. Analyze Failed Logins with KQL
In Log Analytics → Logs, run:
let GeoIPDB_FULL = _GetWatchlist("geoip"); let WindowsEvents = SecurityEvent 
| where EventID == 4625 
| order by TimeGenerated desc 
| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network); WindowsEvents 
| project TimeGenerated, Computer, AttackerIp = IpAddress, cityname, countryname, latitude, longitude, Activity

   ![Resource Group Screenshot](../Document_Images/image7.png)

---


## 10. Visualize with Workbooks
1. Navigate to Sentinel → Workbooks

2. Add a Map visualization using the query results

	{
		"type": 3,
		"content": {
		"version": "KqlItem/1.0",
		"query": "let GeoIPDB_FULL = _GetWatchlist(\"geoip\");\nlet WindowsEvents = SecurityEvent;\nWindowsEvents | where EventID == 4625\n| order by TimeGenerated desc\n| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)\n| summarize FailureCount = count() by IpAddress, latitude, longitude, cityname, countryname\n| project FailureCount, AttackerIp = IpAddress, latitude, longitude, city = cityname, country = countryname,\nfriendly_location = strcat(cityname, \" (\", countryname, \")\");",
		"size": 3,
		"timeContext": {
			"durationMs": 2592000000
		},
		"queryType": 0,
		"resourceType": "microsoft.operationalinsights/workspaces",
		"visualization": "map",
		"mapSettings": {
			"locInfo": "LatLong",
			"locInfoColumn": "countryname",
			"latitude": "latitude",
			"longitude": "longitude",
			"sizeSettings": "FailureCount",
			"sizeAggregation": "Sum",
			"opacity": 0.8,
			"labelSettings": "friendly_location",
			"legendMetric": "FailureCount",
			"legendAggregation": "Sum",
			"itemColorSettings": {
			"nodeColorField": "FailureCount",
			"colorAggregation": "Sum",
			"type": "heatmap",
			"heatmapPalette": "greenRed"
			}
		}
		},
		"name": "query - 0"
	}

   	 ![Resource Group Screenshot](../Document_Images/image10.png)

3. Configure title, grouping, and save the workbook

     ![Resource Group Screenshot](../Document_Images/image18.png)

---
     
## 11. Daily Report Example
Showcases attack volume (e.g., 6.5k attempts in one day):

   ![Resource Group Screenshot](../Document_Images/image20.png) 

## 🎥 Demo Video
The following short video demonstrates running a KQL query in Microsoft Sentinel and visualizing failed login attempts on a world map.

(https://youtu.be/DvFc_cODpQk)

---

## Summary
This lab demonstrates:

- Azure VM setup for Active Directory testing

- Integration with Microsoft Sentinel for log analysis

- Basic use of KQL and visualization workbooks

- GeoIP enrichment and attack monitoring

Now you're ready to start testing and analyzing AD-focused attack scenarios!
