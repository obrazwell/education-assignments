# Getting Started with Terraform

Terraform is a tool for managing infrastructure as code (IaC). This guide offers a high level view of some of the basics to get you started with using Terraform. Using this guide you will learn how to install Terraform, create a Directory/Path for your infrastructure, and learn about some of the basic commands within Terraform.

## Prerequisites for Installing and Using Terraform

- Compatible operating system
- Sufficient memory
- Network that is enabled for incoming and outgoing traffic
- Understanding of how to use a Command-Line-Interface (CLI)

## Install Terraform

To install Terraform manually, visit [Terraform.io](https://developer.hashicorp.com/terraform/install) and click the download link that corresponds to the operating system and processor of your device. This will initiate the download of a compressed (.zip) file to your device.

Once the installation package is downloaded to your device, extract the zip file and place the terraform executable and place the terraform executable in a directory included in your system’s PATH. For example, on Linux or macOS, move the binary to /usr/local/bin:

Terraform can also be installed using a package manager.

For a complete tutorial on how to install Terraform for your specific device and/or package installer, visit:

[Install Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)


## Create a New Directory

When Terraform is installed, you can start creating infrastructure.

You can create a new working directory on your local machine and move to that directory with the following commands:

```shell
$ mkdir terraform-demo
$ cd terraform-demo
```

## Create a Terraform (.tf) File

When in your working directory, you can create a file for your Terraform configuration code with the following command:

```shell
$ touch main.tf
```

Once you have created the .tf file, you can begin writing a configuration. For an example, paste the following lines into the file you created:

```hcl
terraform {
  required_providers {
    docker = {
      source = "kreuzwerker/docker"
    }
  }
}
provider "docker" {
    host = "unix:///var/run/docker.sock"
}
resource "docker_container" "nginx" {
  image = docker_image.nginx.latest
  name  = "training"
  ports {
    internal = 80
    external = 80
  }
}
resource "docker_image" "nginx" {
  name = "nginx:latest"
}
```

## Initialize Command

Initialize Terraform with the `init` command. This will initialize the working directory you created and make it possible to run other Terraform commands. 

```shell
$ terraform init
```

## Apply Command

If the init command runs successfully, you can create or update your infrastructure with the `apply` command.

```shell
$ terraform apply
```

The `apply` command will take up to a few minutes to run. When completed, a message will display indicating that the resource is created.

## Destroy Command

You can destroy any infrastructure you have created with the following command.

```shell
$ terraform destroy
```

Look for a message at the bottom of the output asking for confirmation. Type `yes` and hit ENTER. Terraform will destroy the resources it created earlier.

## Next steps

You should now have a basic understanding of how to install Terraform and some of the basic commands. Terraform is a tool for IaC that enables you to setup infrastructure in a scalable and repeatable fashion, reducing the time involved and risk for human error involved in setting up infrastructure manually. Now that you have Terraform installed, you can use the following guides to learn about how to begin managing resources in your cloud based infrastructure using Terraform. 

[Intro to Terraform](https://developer.hashicorp.com/terraform/intro)

[Terraform Language](https://developer.hashicorp.com/terraform/language)

[Terraform Sandbox](https://developer.hashicorp.com/terraform#sandbox)

[Terraform CLI](https://developer.hashicorp.com/terraform/cli/commands)



