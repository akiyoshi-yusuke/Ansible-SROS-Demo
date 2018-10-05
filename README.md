# Ansible-SROS-Demo
Example Playbooks for Nokia SR OS Routers

## Example 1

Retrieve state information using NETCONF using nokia-state module.

```
├── nctest01.yml
└── roles
    ├── nctest01
    │   └── tasks
    │       └── main.yml
```

## Example 2

Creation of customer "alpha" using NETCONF with nokia-conf module. XML code is embedded in tasks/main.yml file. Edit-config operation "create" is used. Returns an error if the customer already exists.

```
├── nctest02.yml
└── roles
    ├── nctest02
    │   └── tasks
    │       └── main.yml
```

## Example 3

Deletion of customer "alpha" using NETCONF with nokia-conf module. XML code is contained in separate delete_customer_10.xml file. Edit-config operation "delete" is used. Returns an error if the customer does not exist.

```
├── nctest03.yml
└── roles
    ├── nctest03
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       └── delete_customer_10.xml
```

## Example 4

Deletion of customer "alpha" using NETCONF with nokia-conf module. XML code is contained in separate XML file. Edit-config operation "remove" is used. Returns no error if the customer does not exist.

```
├── nctest04.yml
└── roles
    ├── nctest04
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       └── remove_customer_10.xml
```

## Example 5

Creation of customer "demo" and a list of VPLS services using NETCONF with the nokia-conf module. XML code is auto-rendered using the create_vpls.xml Jinja2 template. VPLS service data is contained in the defaults/main.yml file.

Edit-operation "replace" is used. All pre-existing customer and services configured are replaced by the new configuration. Returns no error if the customer or services do already exist.

This example is just providing the key-values "customer-name" and "service-name". The numeric identifiers "customer-id" and "service-id" are automatically created using "md-auto-id". Those auto-created values are not persisted and might change when rebooting the node.

```
├── nctest05.yml
└── roles
    └── nctest05
        ├── defaults
        │   └── main.yml
        ├── tasks
        │   └── main.yml
        └── templates
            └── create_vpls.xml
```

