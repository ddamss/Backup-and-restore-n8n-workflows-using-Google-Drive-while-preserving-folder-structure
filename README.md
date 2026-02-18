# Backup-and-restore-n8n-workflows-using-Google-Drive-while-preserving-folder-structure
Backup your entire n8n automation project, including nested folders and workflows, to Google Drive and easily restore it to n8n. Preventing data loss from accidental deletion or errors, especially critical for self-hosted setups.

# A.  Back up n8n workflows to Google Drive while preserving folder structure

Backup your entire n8n automation project—including nested folders and workflows—to Google Drive, preventing data loss from accidental deletion or errors, especially critical for self-hosted setups.

> Workflow template can either be found
> 	- in n8n : https://n8n.io/workflows/13245-back-up-n8n-workflows-to-google-drive-while-preserving-folder-structure/
> 	- or in github above JSON file : [back-up-n8n-workflows-to-google-drive-while-preserving-folder-structure.json](https://github.com/ddamss/Back-up-n8n-workflows-to-Google-Drive-while-preserving-folder-structure/blob/main/back-up-n8n-workflows-to-google-drive-while-preserving-folder-structure.json#L8)

## ✅ What problem does this workflow solve?

If you’re building and managing multiple automations with well-organized nested folders structure, then, losing a workflow due to accidental deletion or misconfiguration, can cost you hours of work and headache.

This can be even more impactful for self-hosted n8n instances.

This template solves that for any n8n setup (cloud or self hosted) by exporting a perfect mirrored setup of a whole n8n project, preserving the nested folder structure and the workflows within it.

All of it is uploaded in google drive under one main backup folder per execution to keep track of different setup versions along time.

## 🧑‍💻Who’s it for ?
This workflow is ideal for any n8n user, from beginner to advanced solo/team “flowgrammer” who wants to have a reliable, safe, automated and easy to access backup solution that reflects a perfect mirror of their n8n setup.

## ✨What it does 

- **Scheduled Execution** : The workflow runs automatically according to the schedule, could be up to X times a day (or can be triggered manually).

- **Creates backup Folder** : It creates a new overall backup folder with a naming convention as “n8n_backup_folder_structure_DDMMYYYY_HHmmss” (i.e “n8n_backup_folder_structure_02022026_123343”) where the whole n8n nested folder structure along with workflows (JSON files) will be saved.

For example if an n8n workflow instance look like this, then same structure will be preserved and reflected on google drive along with the workflows within each folder :

```
 projects-root-folder/
	└── Your-project-folder-name/
		└── Utilities/
└──Error_management
	└── error_alerting.json
└──Log_analysis
└── Reports/
	└── Clients
		└──Client_A
		└──Client_B
└── client_reporting_standard.json
       └── ...
└── workflow_test.json
```

- **Fetches the non documented n8n API** : It connects to your n8n instance via the n8n API, not the documented one, but the one used directly from your UI when you manipulate your instance.
This API has been used instead of the native n8n node because it gives some more features that are being used here such as :

   - Retrieve the workflow’s parentFolder name
   - Retrieve the workflow’s description
   - Retrieve the n8n instance’s projectId
   - Create an n8n data table
   - Get properties of an n8n data table

## 🛠️How to set up?

1. **Configure Credentials**: Make sure you have valid credentials for:

**Google Drive**: To allow the workflow to create folders and upload files.

2. **Set Your Variables**: In the first Set node named "n8n instance/project access details":

   - `n8n_instance_URL`: Paste your n8n instance URL without the “/” at the end. For example : https://myautomations.app.n8n.cloud
   - `emailOrLdapLoginId`: your login email address
   - `password`: your password

<img width="193" height="190" alt="image" src="https://github.com/user-attachments/assets/4e060a7c-6536-4ded-a894-327d884a7f89" />
<img width="372" height="313" alt="image" src="https://github.com/user-attachments/assets/bf38be74-069e-491b-962d-d9a624ba79af" />


3. **Create your main backup folder**: Create on your google drive space the main folder where all your backup will be uploaded. For example “my_n8n_backup” and then select it in the node `Create backup folder"n8n_backup_folder_structure_ddMMyyyy_HHmmss"` from the List under “Parent Folder”,

<img width="295" height="181" alt="image" src="https://github.com/user-attachments/assets/968fdaac-fae9-46dc-9986-d1f8c1261e62" />
<img width="715" height="427" alt="image" src="https://github.com/user-attachments/assets/7262bfa1-4d77-4a04-8814-6a844b11ed6c" />


### 🚀Activate the workflow, and you're all set!

# B. Restore Backup workflows to n8n from google Drive

You can run it manually by selecting a specific backup folder name from your google drive, to you want to restore on n8n.

<img width="172" height="144" alt="image" src="https://github.com/user-attachments/assets/e037d33b-948f-48de-ae11-3094c0d27d5c" />

<img width="613" height="582" alt="image" src="https://github.com/user-attachments/assets/e27e5a19-002c-4658-ba85-6fe47f946cc9" />

After running the workflow you'll see on your n8n the backup folder restore with all your saved folder/subfolders and associated workflows.

<img width="970" height="177" alt="image" src="https://github.com/user-attachments/assets/5dd83925-02e3-4f87-807d-15b045fc10a1" />

And when you open that folder you'll see all your setup restored ! 

<img width="996" height="619" alt="image" src="https://github.com/user-attachments/assets/15e4f77e-3795-4af5-a3b6-2aa98b05cf2b" />
