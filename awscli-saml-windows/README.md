
# awscli-saml-windows

**Purpose:**
Working with AWS CLI on Windows using saml token via Chocolatey Package Manager

**Pre-requisite installations:**
- Chocolatey
- AWS CLI
- SAML2AWS

**Procedure:**
1. Install chocolatey by following steps on this link 
`https://chocolatey.org/docs/installation`
2. Install AWS CLI on desired version using the command
`choco install awscli --version=1.14`
3. Install saml2aws
`choco install saml2aws`
4. Configure saml2aws to federation link

```PS C:\Users\villam> saml2aws configure
? Please choose a provider: ADFS
? Please choose an MFA Auto
? AWS Profile saml
? URL https://sample-adfs-federatedlink/adfs/ls/IdpInitiatedSignOn.aspx
? Username useremailaddress
? Password ***************
? Confirm ****************

```

**How to login with saml2aws**

Run `saml2aws login`
Once authenticated with correct credentials, you will now be provided with the list of ADFS accounts. Scroll and hit enter on desired account.
```PS C:\Users\villam> saml2aws login
Using IDP Account default to access ADFS https://sample-adfs-federatedlink/adfs/ls/IdpInitiatedSignOn.aspx
To use saved password just hit enter.
? Username useremailaddress
? Password *****************

Authenticating as useremailaddress ...
? Please choose the role  [Use arrows to move, type to filter]
```

To eliminate login prompts:
Run `saml2aws login --skip-prompt --profile=$AWS_PROFILE --role=$ROLE`

Ex. saml2aws login --skip-prompt --profile=aws-sampleaccount --role=arn:aws:iam::1111113333:role/ADFS-EnterpriseAdmin

To re-enforce login (a new access key pair with be stored in the AWS Configuration) :
Run `saml2aws login --skip-prompt --profile=$AWS_PROFILE --role=$ROLE --force`

Ex. saml2aws login --skip-prompt --profile=aws-sampleaccount --role=arn:aws:iam::1111113333:role/ADFS-EnterpriseAdmin --force
