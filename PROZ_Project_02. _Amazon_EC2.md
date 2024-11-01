<h3>PROZ AWS Arquitet@s Program</h3>
<h1> Create a simple <code><em>EC2</em></code> instance.</h1>
<p>October 21, 2024<br></p>

<h2>Created key pair: <strong><em></em><code>rosana-santos-keys-proz</em></code></strong></h2>

<pre><code>aws ec2 create-key-pair --key-name elfo --output text > C:\[REDACTED]\elfo.pem</code></pre>


![image](https://github.com/user-attachments/assets/722bebe1-aaba-4b01-97c1-b00cc0e3c645)




<h2>Created an EC2 instance: <strong><em></em><code>ec2-rosana-santos-proz</em></code></strong></h2>
<pre><code>C:\Windows\System32>aws ec2 run-instances --image-id ami-0989c1b438266c944 --count 1 --instance-type t2.micro --key-name rosana-santos-keys --security-group-ids sg-048adbbb7cda6e319 --subnet-id subnet-06275e0cf1c1039ae --associate-public-ip-address --block-device-mappings "[{\"DeviceName\":\"/dev/xvda\",\"Ebs\":{\"VolumeSize\":8,\"VolumeType\":\"gp3\"}}]" --tag-specifications "ResourceType=instance,Tags=[{Key=Name,Value=ec2-rosana-santos-proz}]"</code></pre>


<p>The output indicates that my EC2 instance has been successfully created. Here are key details confirming the setup:
AMI: ami-0989c1b438266c944 (Amazon Linux 2023)<br>
Instance Type: t2.micro<br>
Key Pair: rosana-santos-keys<br>
Security Group: rosana-santos-proz (sg-048adbbb7cda6e319), allowing HTTP and SSH as required.<br>
Subnet: subnet-06275e0cf1c1039ae (Public subnet)<br>
Tags: Name set to ec2-rosana-santos-proz<br>
Block Device: Configured correctly as DeviceName=/dev/xvda<br>
The instance state is initially "pending", which means it's in the process of launching. It should transition to "running" soon after.</p>

<pre><code>
{
    "Groups": [],
    "Instances": [
        {
            "AmiLaunchIndex": 0,
            "ImageId": "ami-0989c1b438266c944",
            "InstanceId": "i-05297d684c53e0c2c",
            "InstanceType": "t2.micro",
            "KeyName": "rosana-santos-keys",
            "LaunchTime": "2024-10-21T21:42:40+00:00",
            "Monitoring": {
                "State": "disabled"
            },
            "Placement": {
                "AvailabilityZone": "sa-east-1a",
                "GroupName": "",
                "Tenancy": "default"
            },
            "PrivateDnsName": "ip-172-20-16-86.sa-east-1.compute.internal",
            "PrivateIpAddress": "172.20.16.86",
            "ProductCodes": [],
            "PublicDnsName": "",
            "State": {
                "Code": 0,
                "Name": "pending"
            },
            "StateTransitionReason": "",
            "SubnetId": "subnet-06275e0cf1c1039ae",
            "VpcId": "vpc-0e33f5da409fa3d35",
            "Architecture": "x86_64",
            "BlockDeviceMappings": [],
            "ClientToken": "165cc2cb-444f-477b-9e82-7bccf4504e63",
            "EbsOptimized": false,
            "EnaSupport": true,
            "Hypervisor": "xen",
            "NetworkInterfaces": [
                {
                    "Attachment": {
                        "AttachTime": "2024-10-21T21:42:40+00:00",
                        "AttachmentId": "eni-attach-035ea0ef2d5f147c7",
                        "DeleteOnTermination": true,
                        "DeviceIndex": 0,
                        "Status": "attaching",
                        "NetworkCardIndex": 0
                    },
                    "Description": "",
                    "Groups": [
                        {
                            "GroupName": "rosana-santos-proz",
                            "GroupId": "sg-048adbbb7cda6e319"
                        }
                    ],
                    "Ipv6Addresses": [],
                    "MacAddress": "02:1f:a3:1c:ab:a5",
                    "NetworkInterfaceId": "eni-0852e13193e072b28",
                    "OwnerId": "712107929769",
                    "PrivateIpAddress": "172.20.16.86",
                    "PrivateIpAddresses": [
                        {
                            "Primary": true,
                            "PrivateIpAddress": "172.20.16.86"
                        }
                    ],
                    "SourceDestCheck": true,
                    "Status": "in-use",
                    "SubnetId": "subnet-06275e0cf1c1039ae",
                    "VpcId": "vpc-0e33f5da409fa3d35",
                    "InterfaceType": "interface"
                }
            ],
            "RootDeviceName": "/dev/xvda",
            "RootDeviceType": "ebs",
            "SecurityGroups": [
                {
                    "GroupName": "rosana-santos-proz",
                    "GroupId": "sg-048adbbb7cda6e319"
                }
            ],
            "SourceDestCheck": true,
            "StateReason": {
                "Code": "pending",
                "Message": "pending"
            },
            "Tags": [
                {
                    "Key": "Name",
                    "Value": "ec2-rosana-santos-proz"
                }
            ],
            "VirtualizationType": "hvm",
            "CpuOptions": {
                "CoreCount": 1,
                "ThreadsPerCore": 1
            },
            "CapacityReservationSpecification": {
                "CapacityReservationPreference": "open"
            },
            "MetadataOptions": {
                "State": "pending",
                "HttpTokens": "required",
                "HttpPutResponseHopLimit": 2,
                "HttpEndpoint": "enabled",
                "HttpProtocolIpv6": "disabled",
                "InstanceMetadataTags": "disabled"
            },
            "EnclaveOptions": {
                "Enabled": false
            },
            "BootMode": "uefi-preferred",
            "PrivateDnsNameOptions": {
                "HostnameType": "ip-name",
                "EnableResourceNameDnsARecord": false,
                "EnableResourceNameDnsAAAARecord": false
            },
            "MaintenanceOptions": {
                "AutoRecovery": "default"
            },
            "CurrentInstanceBootMode": "legacy-bios"
        }
    ],
    "OwnerId": "712107929769",
    "ReservationId": "r-05c58a5d49a76045c"
}
</code></pre>

![image](https://github.com/user-attachments/assets/9376cb77-c798-4d99-82af-1d8944166f69)


<h2>Checked instance status</h2>

<p>It is running!!</p>

<pre><code>aws ec2 describe-instances --instance-ids i-05297d684c53e0c2c --query "Reservations[*].Instances[*].State.Name" --output text</code></pre>

![image](https://github.com/user-attachments/assets/7cb88562-dc9d-427a-9b0b-9a9da6dd558a)


To connect to your instance using the Amazon EC2 console
Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.

In the navigation pane, choose Instances.

Select the instance and choose Connect.

Choose the EC2 Instance Connect tab.

For Connection type, choose Connect using EC2 Instance Connect.

If there is a choice, select the IP address to connect to. Otherwise, the IP address is selected automatically.

For Username, verify the username.

Choose Connect to open a terminal window.

![image](https://github.com/user-attachments/assets/57bb3201-c720-47f1-a963-4ef90f505562)





































































