## Route53 CloudFormation Template

This folder has the CloudFormation template to deploy route53 Private Hosted Zone for VPC. This template also deploys the DHCP Options Set and that requires Custom Nameserver server IPs to be passed to the Template.

## Input Parameters

|     Parameters                   |            Description            |
|----------------------------------|-----------------------------------|
|     PrivateHostedZoneNameSuffix  |  Suffix of the domain Name for the Private hosted zone in Route53.Leave Empty to create public hosted zone|
|     PublicHostedZoneNameSuffix   |  Suffix of the domain Name for the Private hosted zone is Route53.Leave Empty to create private hosted zone|
|     Environment                  |  Prefix used for naming the resources created in the stack with the format ${Environment}-<resource>. For example, if it was set to svc, then the resources would have a name svc-resource. It must contain only lower case letters and minimum string length is 2.        |
|     BindDnsServer0               |  Bind DNS Server0 IP. Leave empty if you want to use the AmazonProvidedDNS.             |
|     BindDnsServer1               |  Bind DNS Server1 IP. Leave empty if you want to use the AmazonProvidedDNS.             |
|     SetDHCPOptions               |  Whether to create DhcpOptions and assign to VPC.                                       |

## Resources

The template creates the following resources:
- PublicHostedZone : Its created only if `PublicHostedZoneNameSuffix` passed as a parameter.
- PrivateHostedZone
- DHCP Option Set like DhcpOptionsBind, DhcpOptionsAmazon: The DHCP Options set with Bind Servers are created when the Bind Server IPs are passed and if the Bind Servers IPs are not passed then the DHCP Options Set is created with Amazon Provided DNS.


## Authors
* **Bharat Puri**  -  *bhpuri@gmail.com*  

## License

This project is licensed under the MIT License - see the [LICENSE.md](../LICENSE.md) file for details
