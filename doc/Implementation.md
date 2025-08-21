# Input

The input file is in csv format stored in the *\<input_folder\>*

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
Both the log file and version files are stored in *\<output_folder\>*  
\* means the column may not be implemented.
## Updated log file
| Column Name               | Data Type | Description |
|---------------------------|-----------|-------------|
| id                  | integer    | Row index |
| changetime                  | date    | Updated time |
| variable                       | string    | Updated variable |
| bin                       | string    | Updated bin |
| ori_group_id                  | integer    | Group id in the last save  |
| new_group_id                  | integer    | Updated group id  |
| versionfile          | string    | Version file name that stores the result of this change |
| *username          | string    | User who edits the data |

## Version file
Same structure as the input file.


# Design of Version File

# Design of Log File

# Design of Loading Version File
