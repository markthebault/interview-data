# Terraform live questions

This is a set of questions that will increase the difficulty along the way

**Make sure you run terraform to test your code on all questions**

## 1. Create a TLS private key
Using terraform create a TLS private key with `RSA` encryption and `4096` bits. You **must use** the hashicorp tls provider.

## 2. Create a Tls certificate
In the same file, create a tls self signed certificate that will use the key you previously generated. You will still be using the same provider.

You must set the follwing values, you will need to find the appropriate variables to set:
```javascript
COMMON NAME = "testterraform.com"
ORGANIZATION = "terraform"
EXPIRE ON = now + 10 years
```

## 3. Loop me in
The next section if to assess the possibility of creating several certificates from a map.

Use a variable called `certificates` where you can specify the values above for each certificate you will generate.

You can set the values of this variable either by using **defaults** or using `terraform.tfvars`

Example:
```javascript
// Example of values that can be passed in terraform.tfvars
certificates={
  cert1 = {
    param1 = "...."
    param2 = "...."
    param3 = "...."
  },
  cert2 = {
    param1 = "...."
    param2 = "...."
    param3 = "...."
  },
  cert3 = { .... }
}

```

## 4. Output
Add the certificates generated in a previous section in a `terraform output` for later use. This variable should contain the map of all the certificated you generated previously.

## 5. Terraform Module
Create a terraform module with code you created previously. Use another file to call this module.

## 6. Terraform module improvements
Now it is time to make sure your module is generating the certificated in the way we need them for different usecases, your requirement is to have those entry variables:

***Note: if no variables are used, use some defaults***

```javascript
// INPUT
module "self_signed_certs" {
  source = "./modules/self_signed_certs"

  server_certificates ={
    server_1 = {
      common_name = "terraform.interview"
      organization = "Allianz"
      validity = 8760
    }

    server_2 = {
      common_name = "tf.int"
    }
  }
}

// MODULE OUTPUT
server_certificates = {
  "server_1" = {
    "tls_certificate" = ...
    "tls_private_key" = ...
  },
  "server_2" = {
    "tls_certificate" = ...
    "tls_private_key" = ...
  }
}
```

