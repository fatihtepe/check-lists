## This template will create Application Load Balancer with ASG and LT.

![img1.png](./img/img1.png)
```
- write `cfn` and select `cfn-lite` 
- Delete `parameters`
- Delete `outputs`
- `|` pipe (near Descriptions) let me write multiple lines
- Write a description under `Description` title ==> (This template will create Application Load Balancer with ASG and LT.)
```
![img1.png](./img/img2.png)
```
- `Resources:` ==> go under resources
- write `secgr` within list select `ec2-securitygroup`
- `LogicalID` it is like a variable and change it as `CallSecGroup` 
- keep the `Type` ==> every resources has a type
- `GroupDescription:` write what secgroup does ==> 'Enables SSH and HTTP ports` # Required  
- Delete `GroupName` # not required
- Delete `SecurityGroupEgress` ==> outbound group (*security groups are stateful)
- `SecurityGroupIngress` add rules under it list of rules to that..
- under `SecurityGroupIngress` write ingress(a list will popup) and select `security-group-ingress-cidr` 
- For `IpProtocol` select `tcp`
- `FromPORT: 22`
- `ToPort: 22`
- `CidrIp: 0.0.0.0/0`
- `IpProtocol: tcp`
- `FromPORT: 80`
- `ToPort: 80`
- `CidrIp: 0.0.0.0/0` 
- Delete `Tags` 
- `VpcId !Ref CallVPC` ==> we need to define VPC and call it with !Ref*  
```
![img3.png](./img/img3.png)

```
- under `Resources` write `target` (list popup) select `elasticloadbalancingv2-target..`
- rename `LogicalId` as `CallAlBTargetGroup`
- `Type: AWS::ElasticLoadBalancingV2::TargetGroup`
- `Properties:`
- `HealthCheckIntervalSeconds: 25`
- `HealthCheckTimeoutSeconds: 4`
- `HealthyThresholdCount: 3`
- `Port: 80`
- `Protocol: HTTP`
- `TargetType: instance`
- `UnhealthyThresholdCount: 3`
- `VpcId: !Ref CallVPC` ==> we need to define VPC and call it with !Ref*
- DELETE all other lines under `CallAlBTargetGroup` <==(LogicalId)
```
![img4.png](./img/img4.png)
```
- Go top under `Description:` 
- write `Parameters:`
- write `para` under `Parameters` (list popup) select `parameter-type-vpc-id` 
- rename `ParameterName` variable as `CallVPC`
- define `Description:`=> `Select the VPC for your application from the list.`
- keep `Type` as is. 
- Delete `Default`
```
![img5.png](./img/img5.png)
```
- go under `CallAlBTargetGroup`
- write `elasticload` (list popup) select `elasticloadbalancingv2-loadbal...` enter
- rename `LogicalId` as `CallApplicationLoadBalancer:`
- keep `Type:` under `CallApplicationLoadBalancer:` as is
- keep the 'Type' bottom  and rename `String` as `application`
- keep `Properties`
- under `Properties` I defined SecurityGroups before and I need `IDs` of security group*   
- `!GetAtt CallSecGroup.GroupId` previously defined `CallSecGroup` and attribute `GroupId` 
- keep `Subnets:' and Go Top Under `Parameters` define subnet lists and we will use `!Ref CallSubnets` here. 
- DELETE all other lines under `CallApplicationLoadBalancer:` <==(LogicalId)
```
![subnets](./img/img8.png)
```
- under Parameters write `para` (list pop) we need more than one subnet therefore we will select `parameter-type-subnet-id-list` List means we can select more than one.
- rename `paramName` variable as `CallSubnets:`
- keep `Description` write `Please select at least two of the subnets from the list.`
- keep 'Type` as is
- Delete `Default`
```
![listener](./img/img9.png)








<br>
<br>
--------------------------------------------------------------------------------

* [Security groups are stateful](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)—if you send a request from your instance, the response traffic for that request is allowed to flow in regardless of the inbound rules. This also means that responses to allowed inbound traffic are allowed to flow out, regardless of the outbound rules.

* VPC ==> All our resources should be under same VPC you need to define VPC id here. Then, resources (secgroup, targetgroup) can talk each other.  

* ![SecurityGroups IDs](./img/img6.png) `CallApplicationLoadBalancer's` securityGroups IDs 

* ![GetAtt](./img/img7.png) `!GetAtt` function