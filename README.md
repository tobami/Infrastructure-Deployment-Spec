Description
===========
This specification aims to augment [Chef's](http://wiki.opscode.com/display/chef/Home) Configuration Managment with infrastructure provisioning, to fully deliver on the promise of "Infrastructure as code".

Amazon's Web Services [recent outage](http://agilesysadmin.net/ec2-outage-lessons) has paradoxically highlighted the need for a tool like [AWS CouldFormation](http://aws.amazon.com/documentation/cloudformation/) that is vendor independent.

There are already Open Source cloud-agnostic libraries for cloud APIs (Fog, libcloud...), and several tools that make use of it (Chef's knife, Spiceweasel)but a infrastructure specification is still missing.

An example of how the specification could look like (from example.json):

```javascript
{
    "speficication_version": "0.1",
    "deployment_version": "1.0",
    "nodes": [
        {
            "Name": "Master DB",
            "Description": "This node will host the Master DB",
            "Provider": "Rackspace",
            "image": "49",
            "machine": "2",
            "zone": "1",
            "Roles": [
                "role[master_db]"
            ],
            "step": 1
        },
        {
            "Name": "Slave DB",
            "Description": "This node will host the Slave DB",
            "Provider": "Rackspace",
            "image": "49",
            "machine": "2",
            "zone": "1",
            "Roles": [
                "role[slave_db]"
            ],
            "step": 2
        },
        {
            "Name": "WebApp",
            "Description": "The Apache web server and our App",
            "Provider": "EC2",
            "image": "ami-014da868",
            "machine": "c1.xlarge",
            "zone": "us-east-1",
            "Roles": [
                "role[frontend]"
            ],
            "step": 2
        }
    ]
}
```

Go to the [Wiki](https://github.com/tobami/Chef-Deployments-Specification/wiki) and help in defining this specification!
