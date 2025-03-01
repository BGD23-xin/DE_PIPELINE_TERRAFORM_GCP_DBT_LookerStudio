# Operation for terraform

<div align="center">
  <span style="font-size:20px;">This is for the configuration of the VM and running applications remotely.</span>
</div>

## 1.Installation of terraform (Official Installation Guide[terraform](https://developer.hashicorp.com/terraform/install))

```bash
wget https://releases.hashicorp.com/terraform/1.11.0/terraform_1.11.0_linux_amd64.zip
```

Code of test if terraform is installed correctly"
```bash
terraform --version
```
![photo](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/blob/operations/photos/terraform_version.png)

## 2.Creation of [main.tf]() and [variables.tf]() for configuring infrastructure on GCP


```bash
terraform fmt
```