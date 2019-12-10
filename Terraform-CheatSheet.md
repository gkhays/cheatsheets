# Terraform Cheat Sheet

### Execute plan without being prompted for approval

```
terraform apply -auto-approve
```

### Hide password on the command line

If you have a `terraform.tfvars` variable of `password`. Then set an envrironment variable prefixed with `TF_VAR_`.

```
export TF_VAR_password="not so secret"
```

Now when you invoke `terraform apply` you will not be prompted for your password.
