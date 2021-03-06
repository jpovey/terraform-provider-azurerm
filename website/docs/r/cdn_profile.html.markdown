---
layout: "azurerm"
page_title: "Azure Resource Manager: azurerm_cdn_profile"
sidebar_current: "docs-azurerm-resource-cdn-profile"
description: |-
  Create a CDN Profile to create a collection of CDN Endpoints.
---

# azurerm_cdn_profile

Create a CDN Profile to create a collection of CDN Endpoints.

## Example Usage

```hcl
resource "azurerm_resource_group" "test" {
  name     = "resourceGroup1"
  location = "West US"
}

resource "azurerm_cdn_profile" "test" {
  name                = "exampleCdnProfile"
  location            = "West US"
  resource_group_name = "${azurerm_resource_group.test.name}"
  sku                 = "Standard_Verizon"

  tags {
    environment = "Production"
    cost_center = "MSFT"
  }
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) Specifies the name of the CDN Profile. Changing this forces a
    new resource to be created.

* `resource_group_name` - (Required) The name of the resource group in which to
    create the CDN Profile.

* `location` - (Required) Specifies the supported Azure location where the resource exists. Changing this forces a new resource to be created.

* `sku` - (Required) The pricing related information of current CDN profile. Accepted values are `Standard_Verizon`, `Standard_Akamai` or `Premium_Verizon`.

* `tags` - (Optional) A mapping of tags to assign to the resource.

## Attributes Reference

The following attributes are exported:

* `id` - The CDN Profile ID.

## Import

CDN Profiles can be imported using the `resource id`, e.g.

```shell
terraform import azurerm_cdn_profile.test /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/mygroup1/providers/Microsoft.Cdn/profiles/myprofile1
```
