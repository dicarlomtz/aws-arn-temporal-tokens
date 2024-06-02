# aws-sts-temporal-tokens

Script to get AWS STS Temporal Session Tokens. MFA is not enforced, but optional.

## Requirements

- Python 3.7 or newer
- An AWS Account
- AWS configured locally (check that `Acces Key` and `Secret Key` are set on your credentials file) for your user
- If you are using MFA, please check the arn assigned to your device.

## How to use
execute: `python3 aws-sts-temporal-tokens.py`

You can also add arguments:

- If you don't pass a `--profile (-p)` it will assume your default credentials
- If you pass an arn `--mfa-arn (-a)`, then a mfa token `--mfa-token (-m)` is required
- If you don't pass an arn `--mfa-arn (-a)`, but a mfa token `--mfa-token (-m)` is passed, then it will try to pull the arn from `.aws_arn_profiles.json` on your home directory
- You can also specify the expiration time in seconds `--time (-t)`. Default is set to last 8 hours.
- You can also pass an specific profile `--profile (-p)`.

## Your `.aws_arn_profiles.json` file for profiles
If you want to work with different profiles and avoid having to specify arn devices everytime during the script execution, this file should be in your home directory

The structure should be the following: 

```
   {
        "default": [
                {
                        "arn_device": "arn:aws:iam::<account>:mfa/<name>"
                }
        ],
        "my_second_profile": [
                {
                        "arn_device": "arn:aws:iam::<account>:mfa/<name>"
                }
        ],
        "my_third_profile": [
                {
                        "arn_device": "arn:aws:iam::<account>:mfa/<name>"
                }
        ]
  }
```
