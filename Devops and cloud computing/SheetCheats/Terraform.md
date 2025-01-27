

---

### **What is Terraform?**

- Terraform is an Infrastructure as Code (IaC) tool by HashiCorp.
- It allows you to define and provision cloud resources (e.g., servers, databases, networks) using a declarative configuration language (HCL - HashiCorp Configuration Language).

---

### **Key Concepts**

1. **Providers**:
    
    - Plugins to interact with cloud services (AWS, Azure, GCP, etc.).
    - Example:
        
        ```hcl
        provider "aws" {
          region = "us-west-2"
        }
        ```
        
2. **Resources**:
    
    - Define what infrastructure you want to create (e.g., an EC2 instance, S3 bucket).
    - Example:
        
        ```hcl
        resource "aws_s3_bucket" "example" {
          bucket = "my-unique-bucket-name"
          acl    = "private"
        }
        ```
        
3. **State**:
    
    - Terraform keeps a state file (`terraform.tfstate`) to track the real-world infrastructure.
4. **Variables**:
    
    - Use variables to parameterize configurations.
    - Example:
        
        ```hcl
        variable "region" {
          default = "us-west-2"
        }
        ```
        
5. **Outputs**:
    
    - Extract information after resource creation.
    - Example:
        
        ```hcl
        output "bucket_name" {
          value = aws_s3_bucket.example.bucket
        }
        ```
        

---

### **Getting Started**

1. **Install Terraform**:
    
    - Download from [terraform.io](https://www.terraform.io/downloads).
2. **Basic Workflow**:
    
    - **Write Configuration**: Create `.tf` files.
    - **Initialize**: Install necessary providers.
        
        ```bash
        terraform init
        ```
        
    - **Plan**: Show the execution plan.
        
        ```bash
        terraform plan
        ```
        
    - **Apply**: Apply the configuration.
        
        ```bash
        terraform apply
        ```
        
    - **Destroy**: Remove resources.
        
        ```bash
        terraform destroy
        ```
        

---

### **Basic Example**

#### File: `main.tf`

```hcl
provider "aws" {
  region = "us-west-2"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "ExampleInstance"
  }
}
```

#### Commands:

1. Initialize:
    
    ```bash
    terraform init
    ```
    
2. Check Plan:
    
    ```bash
    terraform plan
    ```
    
3. Apply Changes:
    
    ```bash
    terraform apply
    ```
    

---

### **Key Commands**

- **Format Code**:
    
    ```bash
    terraform fmt
    ```
    
- **Validate Configuration**:
    
    ```bash
    terraform validate
    ```
    
- **Show State**:
    
    ```bash
    terraform show
    ```
    

---

### **Terraform File Structure**

- **Main Configuration**: `main.tf`
- **Variables**: `variables.tf`
- **Outputs**: `outputs.tf`
- **State**: `terraform.tfstate`

---

### **Variables Example**

#### File: `variables.tf`

```hcl
variable "instance_type" {
  default = "t2.micro"
}

variable "region" {
  default = "us-west-2"
}
```

#### File: `main.tf`

```hcl
provider "aws" {
  region = var.region
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = var.instance_type
}
```

---

### **Terraform Modules**

- A way to reuse configurations.
- Example:
    
    ```hcl
    module "network" {
      source = "./modules/network"
      vpc_id = "vpc-12345"
    }
    ```
    

---

### **Key Takeaways**

- Terraform is declarative: define what you want, and it handles the rest.
- State file is crucial—don’t lose it!
- Reuse modules for complex setups.

Let me know if you want to dive deeper into any section!