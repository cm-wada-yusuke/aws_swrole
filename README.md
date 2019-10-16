# aws_swrole

Switch AWS IAM Roles to set envriomnent variables.

## Requirements

This plugin use these command line tools.

* [aws/aws\-cli: Universal Command Line Interface for Amazon Web Services](https://github.com/aws/aws-cli)
* [stedolan/jq: Command\-line JSON processor](https://github.com/stedolan/jq)
* [jorgebucaran/fish\-getopts: Parse CLI options in fish\.](https://github.com/jorgebucaran/fish-getopts)

## Install

Use [fisher](https://github.com/jorgebucaran/fisher)

```
fisher add jorgebucaran/fish-getopts
fisher add cm-wada-yusuke/aws_swrole
```

## Usage

```fish
aws_swrole [-o] <aws profile>
```

* Print AWS_XXX environments commands with -o option.
* Without -o option to set AWS_XXX environments.

## Example

```fish
$ aws_swrole
Usage: swrole [-o] <aws profile>

Defined profiles:
  development
  test
  staging
  production
```

```fish
$ aws_swrole development   
Enter MFA code > 123456

$ aws dynamodb list-tables --region ap-northeast-1
{
   "TableNames": [
       "Movies"
   ]
}
```

```fish
$ aws_swrole -o test
Enter MFA code > 123456
set -x AWS_ACCESS_KEY_ID XXXXXXXXXXXXXXXXXX
set -x AWS_SECRET_ACCESS_KEY YYYYYYYYYYYYYYYYYYYYYYYY
set -x AWS_SESSION_TOKEN ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
```

[slack-badge]: https://fisherman-wharf.herokuapp.com/badge.svg
[fisherman]: https://github.com/fisherman/fisherman
