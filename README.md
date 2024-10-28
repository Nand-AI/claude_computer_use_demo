# claude-computer-use-demo

## Steps for MacOS only
0. `rye sync`
1. Get AWS session token
 * Go to [nand repo](https://github.com/Nand-AI/nand/) local root dir and run below command
 ```
 rye run aws sts get-session-token --duration-seconds 36000 | jq -r '.Credentials | "AWS_ACCESS_KEY_ID=\(.AccessKeyId) AWS_SECRET_ACCE
SS_KEY=\(.SecretAccessKey) AWS_SESSION_TOKEN=\(.SessionToken) AWS_REGION=us-west-2 rye run demo"' | pbcopy
 ```
 * This will copy the command that needs to run in current root dir

2. Run the copied command in current root dir

3. Try ask Claude to do things like: (click reset button to clear context)
 * `Open Safari and try to find information regarding Nand AI company, then give a summary`
 * `Use bash to check k8s pod status and report if any issue`
