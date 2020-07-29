<NavColumns>
<NavColumn>
<ColumnTitle>1. Confirm to accept the peer connection request in your AWS console. </ColumnTitle>

1.1. Sign in the AWS console

![Sign-in-aws](/peering/img/sign-in-aws.png)

1.2. Click on `Services` in the top navigation bar, and input `VPC` to search.

![Services](/peering/img/vpc-search.jpg)

1.3. Click `Peering Connections`,  select the right peer connection according to the peering id and accept it.

![Accept](/peering/img/accept-peering.jpg)

</NavColumn>

<NavColumn>
<ColumnTitle>2. Add a route to the TiDB Cloud VPC for each of your VPC subnet route tables.</ColumnTitle>

2.1. Click `Route tables`,  select the right route tables according to your VPC id. 

![Select-route-tables](/peering/img/select-route-tables.png)

2.2. Select the submenu `Routes`,  and click `Edit routes`.

![Find](/peering/img/edit-route.jpg)

2.3. Edit routes and commit.

![Edit-route](/peering/img/edit-route.jpg)

</NavColumn>


<NavColumn>
  
<ColumnTitle>3、Make sure you have enabled private DNS hosted zone support for your VPC.</ColumnTitle>

3.1. Click `Your VPCs`,  select the right vpc according to your VPC id.

![Select-vpc](/peering/img/select-vpc.png)

3.2. Mouse over the selected VPC,  right-click pops up the setting window, and Click `Edit DNS hostnames`;

![Edit DNS hostnames](/peering/img/edit-dns-hostnames.jpg)

3.3. Enable DNS hostnames.

![Enable dns hostnames](/peering/img/enable-dns-hostnames.jpg)

3.4. Mouse over the selected VPC,  right-click pops up the setting window, and Click `Edit  DNS resolution`;

![Edit DNS solution](/peering/img/edit-dns-solution.jpg)

3.5. Enable DNS resolution.

![Enable dns resolution](/peering/img/enable-dns-solution.jpg)

</NavColumn>


<NavColumn>
  
<ColumnTitle>4. Associate your VPC with the private hosted zone of TiDB `tidb-phz-id`. </ColumnTitle>

4.1. Click `Services` in the top navi bar,  and input `Route 53` to search.

![Route 53](/peering/img/route53-search.jpg)

4.2. Click `Hosted zones`,  select the right hosted zone. Input the your VPC ID in the hosted zone detail, and Click `Associate New VPC`.

![Associate](/peering/img/associate.jpg)

</NavColumn>


</NavColumns>
