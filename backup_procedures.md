# backup-procedures
stored procedures for backup related functionality for db2

These stored procedures are used to mark backups that we would like to retain and moving them in COS to prevent them from being deleted by the automated cleanup process.

Inversely, functionality is also added to unmark these backups as well in case we realize we don't want them.

Listing functionality is also added to show backups which we have available to us as well as which ones we have marked for retention, a sample output is shown below.

```
BACKUP         PARTS       RETAIN
-------------- ----------- -----------
20240229215327           6           0
20240303215333           6           0
20240304215356           6           0
20240305215330           6           0
20240306215327           6           0
20240307215329           6           0
20240308215332           6           0
20240309215331           6           0
20240310215328           6           0
20240311215329           6           0
20240312215333           6           0
20240313215333           6           0
20240314215324           6           0
20240315215328           6           0
20240316215327           6           0
20240317215328           6           0
20240318215334           6           0
20240303215333           6           1
20240312215333           6           1
```

The parts field will be used to help the customer determine if the backup they created was complete or not.

## Usage

**SAVE_BACKUP**:

`db2 "call SAVE_BACKUP(20240313215333);"`

**REMOVE_SAVED_BACUP**:

`db2 "call REMOVE_SAVED_BACKUP(20240313215333);"`

**LIST_BACKUP**:

`db2 "select * from table(LIST_BACKUPS());"`

## Restrictions

Any backup which is within 24 hours of being removed (i.e. 1 day or less from exceeding the retention period) will not be saved. This is done as a fail safe to avoid saving large backups which might get removed within the saving process. If this were to happen, this would create garbage/unuseable data into the customers COS, and would require manual cleanup from us.
