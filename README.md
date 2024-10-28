# claude-computer-use-demo
An internel demo repo for testing Claude computer use

## Steps for MacOS only
0. Ensure [rye](https://github.com/astral-sh/rye) is installed, then run `rye sync`
1. Get AWS session token for Bedrock (with Claude 3.5 v2 access granted)
 * We need to run `AWS_ACCESS_KEY_ID=xx AWS_SECRET_ACCESS_KEY=xx AWS_SESSION_TOKEN=xx AWS_REGION=us-west-2 rye run demo`
 * Can go to [nand repo](https://github.com/Nand-AI/nand/) local root dir and run below command. (ensure `jq` is installed)
 ```
 rye run aws sts get-session-token --duration-seconds 36000 | jq -r '.Credentials | "AWS_ACCESS_KEY_ID=\(.AccessKeyId) AWS_SECRET_ACCESS_KEY=\(.SecretAccessKey) AWS_SESSION_TOKEN=\(.SessionToken) AWS_REGION=us-west-2 rye run demo"' | pbcopy
 ```
   - This will copy the command that needs to run in current root dir

2. Run the copied command in current root dir, you'll need to give corresponding permissions to terminal

3. Try ask Claude to do things like: (click reset button to clear context)
 * `Open Safari and try to find information regarding Nand AI company, then give a summary`
 * `Use bash to check k8s pod status and report if any issue`

## Known issues
* `pyautogui` is not working well with Alacritty terminal
* Only QWER layout can work well
