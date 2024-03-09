















UiPath ServiceNow Integration	       





1.	Objective: Automate the process of handling loan requests raised in ServiceNow, including applying for a loan on the loan website, updating input Excel, closing tickets, and notifying administrators in email.
2.	Scope: The automation will cover the entire process from handling loan requests in ServiceNow to updating input data and closing tickets.
3. Process Flow
Step 1: Incident Creation in ServiceNow. Admin raise loan requests in ServiceNow and attached the inputs in Attachment.
Step 2: Bot Execution: The bot monitors ServiceNow for new loan incidents. This has been achieved using Service Now Connection Trigger in Integration Service.
 

Step – 3: Get the Attachment Sys ID:
The Attachment file contains the input data require to raise loan request.
To Download Attachment file, we must have attachment sys_id. By executing sys_attachment API, we can get sys_id for attachment.


API format
https://<Service Now Instance>/api/now/table/sys_attachment? sysparm_query=table_name=incident^table_sys_id=<incident_sys_id>

Method : GET.

Step-4: Download Attachment File :
Once Get the attachment sys_id, use Get Attachment activity to download input request file (LoanRequest.xlsx)

Step – 5:Process the input Data : 
Process the input data with typical UI Automation and update the output in same LoanRequest.xlsx file.

Step – 6 : Update Admin via email:
Update the Admin. Once Process is successfully completed.
In Case Failure, Update the admin to process manually.

Step – 7 : 
Close the ticket, If the process completed successfully by using Update Service Now Record Activity.
In Case Failure, Update the work notes that the request is moved to manual intervention
                                                                                                              
