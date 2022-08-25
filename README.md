# SecureStack Application-Bill-of-Materials GitHub Action

A GitHub Action that creates a bill of materials holistically from all the important components of your application.  This includes source code, thrd-party libraries and AWS cloud resources.  In addition, this BoM will include any vulnerabilities from your source code and cloud stack.

```
name: Example Workflow Using SecureStack ABOM Action
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Create ABOM
        id: abom
        uses: SecureStackCo/actions-abom@v0.1.0
        with:
          securestack_api_key: ${{ secrets.SECURESTACK_API_KEY }}
          securestack_app_id: ${{ secrets.SECURESTACK_APP_ID }}
          severity: critical
```
NOTE - to understand possible values for the action input `flags`, run the SecureStack cli locally:

`$ bloodhound-cli SBOM --help`

## Create your SecureStack API Key and save as GitHub Secret

1. Log in to [SecureStack](https://app.securestack.com) and go to the Profile -> GENERATE KEY screen.
2. Generate an API key and copy the value.
3. Go to Settings for your GitHub repository and click on Secrets at the bottom left.
4. Create a new secret named SECURESTACK_API_KEY_SECRET and paste the value from step 2 into the field.

## Retreiving your SecureStack Application ID

1. Log in to [SecureStack](https://app.securestack.com).
2. Open the application you wish to analyse.
3. Copy the value of the application id on the View Application screen.
4. Paste into the value of the `securestack_app_id` action input for the step using the SecureStack action in your workflow.

## What types of components will this BoM include?
1. All your software components including third-party libraries and frameworks
2. The AWS native resources that this application is actually using (think Ec2, S3, RDS, Cloudfront, ELB, CloudTrail, CloudWatch, Config, GuardDuty)

Made with 💜  by [SecureStack](https://securestack.com)
