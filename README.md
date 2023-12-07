# Salesforce-ScratchOrg-Notes
Notes outlining the use of Salesforce scratch orgs

## Sign up for a developer org
https://developer.salesforce.com/signup

## Create a Salesforce project in VS Code
- From your VS Code desktop app terminal, run:
    - `sf project generate --name myProjectName`
    - (alternate) From the Command Palette, use `SFDX: Create project`

## Log in to Dev Hub & set it as default
- From the VS Code terminal:
    - `sf org login web --set-default-dev-hub --alias my-dev-hub`
    - [source](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_org_commands_unified.htm#cli_reference_org_login_web_unified)

- To view a list of all orgs currently authenticated:
    - `sf org list`
- To view information on your current org:
    > Warning: This command will expose sensitive information that allows for subsequent activity using your current authenticated session.
    - `sf org display`

## Customize the scratch org definition
- file in the generated Salesforce Project is located at `config/project-scratch-def.json` by default
- Scratch Org Definition File Reference [link to SFDX Developer's Guide](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_scratch_orgs_def_file.htm)
    - Samples can be found at the link
    - Useful notes are adding lines such as `"hasSampleData": true` to include sample data in the generated scratch org

## Generate the scratch org
- From the terminal in VS code, run the following command:
    - `sf org create scratch --definition-file config/project-scratch-def.json --set-default --alias my-scratch-org-alias --duration-days 5`
    - This will create a scratch org using the parameters defined in your file as well as switch to the newly created org
        - This org will last for 5 days (default:7 if not specified)
    - It will take a few minutes, and provide a new OrgId as well as a Username.
    - running `sf org display` will provide further details -- be warned, this displays senstive access information such as your Access Token
        - your expiration date can be found in this information

## Accessing your scratch org in VS Code
- As an authenticated org in VS Code, you should be able to select the Org Alias in the bottom left corner of the application window to change target orgs

## Clean up Orgs in VS Code
- `SFDX: Remove Deleted and Expired orgs` (untested)

## References
- [Salesforce Scratch Org Reference](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_scratch_orgs.htm)
- [Salesforce CLI Command Reference](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_unified.htm)
