# Why use it? 
Use Case: As a Customer concerned about updating Cloudhub Patches every month I want to get a list of all CloudhubAPIs MRT version with their (Major.Minor.Patch, including Patch Date) in a Dashboard so that I can make decisions and understand if we are GOOD to go, even before the Mandatory Patches are "automatically applied"

# What is it? listing-all-apis-versions
Three componentes: 
1. A MuleSoft App to list all Cloudhub APIs for an environment and aggregate the PatchDate, then produces a CSV. You need to add your own Credentials to the Property file
![](img/listing-all-apis-versions/blob/main/img/MuleApp-Flow.png)

2. Postman Collection to call that MuleApp. You need to add your own Auth Headers (OrgID and EnvID). This returns the CSV
![]()

3. GoogleSpreadsheet Dashboard, where you paste the CSV and you go to the Dashboards tab to visualize all your APIs patch dates 
![](img/listing-all-apis-versions/blob/main/img/DashboardSpreadsheet.png?raw=true)


# More Context 
1. The Runtime Manager view shows Mule Versions (x.y.z) without the Patch Date (x.y.z PatchDate), unless you go API by API, one by one. You know there are updates pending, but, you want to know if it is patch related 
“Date Modified” includes “Restarts and other updates to the app”. It does not mean last time a Patch was pplied
![](https://github.com/angelalberici/listing-all-apis-versions/blob/main/img/RuntimeManagerScreen.png?raw=true)

2. Using Platform APIs you can retrieve CloudhubAPIs, it won’t have the Patch Date; Customer need to make so advanced Loop logic with a MuleAPI or other programming to be able to get a list with all the patch date info. Below in the left, example of what a Customer gets
![](https://github.com/angelalberici/listing-all-apis-versions/blob/main/img/PlatformAPIsListCloudhubAPIs.png?raw=true)

3. Ideally, when Patch Update is available, you will immediately apply it and run any automated regression tests, without waiting until Mandatory Patch. Realistically, you prefer to plan it, applying it to most important APIs and testing before the automatic update thus having some time in the unlikely scenario there was a bug
