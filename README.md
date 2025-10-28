# Argo CD non-HA Terraform Module

This repository contains one-to-one converted versions of
the [Argo CD](https://github.com/argoproj/argo-cd) **non-HA** kubectl manifests into
native HCL Terraform format.

## Context

Terraform is a powerful tool for managing infrastructure as code. However, many Kubernetes applications provide their
configurations as kubectl manifests, which cannot be used directly with Terraform. This project converts those
Kubernetes manifests into Terraform configurations, allowing you to manage your Kubernetes resources alongside the rest
of your infrastructure using Terraform.

## Features

* Direct conversions from YAML to HCL
* Organized by version tags
* Easy integration into your Terraform workflows

## Using with Terraform

```hcl
module "argocd_non_ha" {
  source = "git::https://github.com/terraform-please/argocd-non-ha.git//v3.2.0-rc4"
}
```

## Using with CDKTF

Update cdktf.json to include the module:

```json
{
  "terraformModules": [
    {
      "name": "argocd-non-ha",
      "source": "git::https://github.com/terraform-please/argocd-non-ha.git//v3.2.0-rc4"
    }
  ]
}
```

Then run `cdktf get` to download the module.

Use the module in your Typescript code:

```typescript
import {ArgoCdNonHa} from "@gen/modules/argocd-non-ha";

new ArgoCdNonHa(this, "argocd_non_ha", {
    namespace: "argocd",
})
```

## Contributing

Feel free to open issues or pull requests for improvements or fixes.
