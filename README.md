# execute-rundeck-job

Small (bash 4+) script to execute a rundeck job and optionally wait for it to complete. Typically utilized in pipelines that do not have built-in Rundeck integration. Passing in job variables is not supported at this time (configure your job to run out of the box).

## Requirements

The script uses curl and jq. On Ubuntu this can be installed via apt: `apt update && apt install curl jq`

## Usage

`./execute-rundeck-job --rd-job-id JOB_ID [--rd-timeout 300] [--rd-url http://127.0.0.1:4440] [--rd-auth-token AUTH_TOKEN]`

If you do not specify all arguments, defaults are used. Defaults are editable under `DEFAULT_` in the script.

| argument name | value type | what it does | required |
| ------------- | ---------- | ------------ | -------- |
| --rd-job-id       | job ID, from Rundeck | specify the job ID to run | yes |
| --rd-timeout      | seconds | if larger than 0, wait N seconds for the job to complete | no (if default set) |
| --rd-url          | URL     | URL to Rundeck | no (if default set) |
| --rd-auth-token   | API Auth Token | use specified auth token | no (if default set) |

## How to get the API Token

Using rd: `rd tokens create -u USERNAME -r ROLE`   

Otherwise get one in the profile settings in Rundeck.
