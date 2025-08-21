# Input Main Dataset

The input main dataset is in csv format stored in the *\<input_folder\>*

| Column Name               | Data Type | Description |
|---------------------------|-----------|-------------|
| variable                  | string    | The name of the variable being analyzed. |
| bin                       | string    | The bin or category of the variable. |
| group_id                  | integer    | Identifier for the group. |
| index_id                  | integer    | Identifier for the index. |
| train_good_count          | integer    | Count of good outcomes within the bin that belong to the training set. |
| train_bad_count           | integer    | Count of bad outcomes within the bin that belong in the training set. |
| train_factored_good_count | number    | Factored count of good outcomes within the bin that belong to the training set. |
| train_factored_bad_count  | number    | Factored count of bad outcomes within the bin that belong to the training set. |
| train_good%               | number    | Percentage of good outcomes within the bin that belong to the training set. |
| train_bad%                | number    | Percentage of bad outcomes within the bin that belong to the training set. |
| train_factored_good%      | number    | Factored percentage of good outcomes within the bin that belong to the training set. |
| train_factored_bad%       | number    | Factored percentage of bad outcomes within the bin that belong to the training set. |
| train_woe                 | number    | Weight of evidence of the bin belong to the training set. |
| train_mc                  | number    | MC of the bin belong to the training set. |
| test_good_count           | integer    | Count of good outcomes within the bin that belong to the test set. |
| test_bad_count            | integer    | Count of bad outcomes within the bin that belong to the test set. |
| test_factored_good_count  | number    | Factored count of good outcomes within the bin that belong to the test set. |
| test_factored_bad_count   | number    | Factored count of bad outcomes within the bin that belong to the test set. |
| test_good%                | number    | Percentage of good outcomes within the bin that belong to the test set. |
| test_bad%                 | number    | Percentage of bad outcomes within the bin that belong to the test set. |
| test_factored_good%       | number    | Factored percentage of good outcomes within the bin that belong to the test set. |
| test_factored_bad%        | number    | Factored percentage of bad outcomes within the bin that belong to the test set. |
| test_woe                  | number    | Weight of evidence of the bin belong to the test set. |
| test_mc                   | number    | Weight of evidence of the bin belong to the test set. |

# Output
Log file and version files are csv files stored in *\<output_folder\>* 
\* means the column may not be implemented.
## Log file
* Columns:
  
  | Column Name   | Data Type | Description                                      |
  |---------------|-----------|--------------------------------------------------|
  | changetime    | date      | Updated time                                     |
  | variable      | string    | Updated variable                                 |
  | bin           | string    | Updated bin                                      |
  | ori_group_id  | integer   | Group id in the last save                        |
  | new_group_id  | integer   | Updated group id                                 |
  | versionfile   | string    | Version file name that stores the result of this change |
  | *username     | string    | User who edits the data                          |

* Filename:  
    *\<main_dataset\>_log.csv*

## Version file
* Columns: Same as the input.
* Filename:   
    * Do not allow customized filename, the file will be named with the current date in the format *\<main_dataset\>_\<YYYYMMDD\>.csv*.    
    Because we will have at most one version per day (according to KS).  
    * The above design will simplify the version management.

# Data Structure for Storing Main dataset, Version File and Editing Data

Use a global variable *working_state* to store data:  
```python
working_state = {
    'original_data': DataFrame,       # Original main data DataFrame
    'current_data': DataFrame,        # Loaded version file and current editing state DataFrame  
    'changes_history': [],       # List of change records in the current editing
    'changes_lasttime':[],       # List of change records in the last time
} 
```

The *changes_history* and *changes_lasttime* stores elements:
```python
change_record = {
    'changetime': date,         # When the change was made
    'variable': string,          # Variable name
    'bin': string,              # Bin value
    'old_group_id': integer,     # Previous group_id
    'new_group_id': integer,     # New group_id
}
```
# Design of UI and Backend
Two dropdown selections:  
* Main Dataset
* Verion

## Values in Main Dataset Selection:
* A list of filenames in *\<input_folder\>*  
The selection will be prefilled with the filename you click on when activating the plugin.

## Values in Version Selection:



### If the user does not choose a version file  
```python
working_state = {
    'original_data': DataFrame,       # Original main data DataFrame
    'current_data': DataFrame,        # Original main data DataFrame
    'changes_history': [],       # List of change records in the current editing
    'changes_lasttime':[],       # List of change records in the last time
} 
```

