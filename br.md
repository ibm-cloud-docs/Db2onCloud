---

copyright:
  years: 2014, 2021
lastupdated: "2021-12-08"

keywords: 

subcollection: Db2onCloud

---

 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Backup and restore
{: #bnr}

## Backup
{: #br_backup}

For paid plans, encrypted backups of the database are done daily. A daily backup is kept for each of the last 14 days.

All paid plans make use of Cross-Regional IBM Cloud Object Storage (COS), by default, to keep backups offsite. {: important}

Changing the backup time can take upto 2 hours to take effect. {: important}

{: shortdesc}

The following is an example of the manual backup operation in the web console UI:

### Enterprise and Standard plans
{: #br_bu_ent_std}

1. Click **Administration** in the left menu and select the **Backups** tab. Click the **Run backup** button.
![View of the highlighted selection of the backup option](images/backup_v2.png "Backup and restore console page"){: caption="Figure 1. Selection of the backup option" caption-side="bottom"}

2. Click **Run** to run a manual backup.
![View of Run Backup page option](images/backup_run_v2.png "Backup and restore console page"){: caption="Figure 2. View of Run backup" caption-side="bottom"}

3. When the backup starts, some features might not be available until the backup is completed.
![View of the backup initiation](images/backup_initiated_v2.png "Backup and restore console page"){: caption="Figure 3. View of the backup initiation" caption-side="bottom"}

4. After backup completion, a new backup entry in the list of backups appears as a **Full (Manual)** type. The new backup is in an available state.
![View of completed backup](images/backup_completed_v2.png "Backup and restore console page"){: caption="Figure 4. View of a completed backup" caption-side="bottom"}


 
## Restore
{: #br_restore}

All paid plans make use of Cross-Regional IBM Cloud Object Storage (COS), by default, to keep backups offsite. {: important}

For information about point-in-time restores, see [Point-in-time restore](#point-in-time).






### End-of-backup restore
{: #br_eobrestore}

#### Enterprise and Standard plans
{: #br_eobr_ent_std}

The following is an example of the end-of-backup restore operation in the web console UI:

1. Click **Administration** in the left menu and select the **Backups** tab. Select a backup that you want to restore to end-of-backup and click **Restore**.
![View of the highlighted selection of the end-of-backup restore option](images/eobrestore_selection_v2.png "Backup and restore console page"){: caption="Figure 5. View of the selection of the end-of-backup restore option" caption-side="bottom"}

2. Click **Restore** to initiate the restore.
![View of Restore backup screen option](images/eobrestore_restore_backup_v2.png "Backup and restore console page"){: caption="Figure 6. View of Restore backup" caption-side="bottom"}

3. An information message appears when restore has started. Some features might not be available until restore is completed.
![Start of the end-of-backup restore](images/eobrestore_started_v2.png "Backup and restore console page"){: caption="Figure 7. Start of the end-of-backup restore" caption-side="bottom"}

4. A progress bar indicates the progress of the restore process.
![Progress of the end-of-backup restore](images/eobrestore_progress_v2.png "Backup and restore console page"){: caption="Figure 8. Progress of the end-of-backup restore" caption-side="bottom"}

5. Notifications show a **Restore success!** message after the restore is completed.
![Successful completion of end-of-backup restore](images/eobrestore_success_v2.png "Backup and restore console page"){: caption="Figure 9. Successful completion of end-of-backup restore" caption-side="bottom"}

### Point-in-time restore
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} added a point-in-time restore capability for systems in {{site.data.keyword.Bluemix_notm}} Public. You can restore to an exact point in time from your backups. 

The following are a selected example of screen captures of the point-in-time restore operation in the web console UI:

#### Enterprise and Standard plans
{: #br_pit_ent_std}

1. Click **Administration** in the left menu and select the **Backups** tab. 

2. Click the down arrow beside the **Run backup** button. Select **Restore (point-in-time)**.
![View of the highlighted selection of the point-in-time restore option](images/pit_restore_pick_v2.png "Backup and restore console page"){: caption="Figure 10. View of the selection of the point-in-time restore option" caption-side="bottom"}

3. Select a point-in-time date to which you want to restore the database. The point-in-time restore process selects the backup closest to your requested point-in-time date out of the pool of retained backups made during the previous 14 days.

   The point-in-time restore process invalidates any of the previously retained backups with dates after the selected point-in-time date because of a resultant divergence in the timeline.
   {: note} 

   ![View of date and time selection for point-in-time restore](images/pit_restore_date_v2.png "Backup and restore console page"){: caption="Figure 11. View of date and time selection for point-in-time restore" caption-side="bottom"}

4. Restoring the database to the selected point in time.
![View of the point-in-time restore initialization](images/pit_restore_progress_v2.png "Initialization of point-in-time restoration"){: caption="Figure 12. View of the point-in-time restore initialization" caption-side="bottom"}

5. The restore operation completed successfully.
![View of the successful completion of the restoration](images/pit_restore_successful_v2.png "Successful completion"){: caption="Figure 13. View of the successful completion of the restoration" caption-side="bottom"}


