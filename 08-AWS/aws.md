- What is VPC ?

    - Virtual Private Cloud (VPC) is a logically isolated network in the  cloud where we can launch the resources(instance etc).and it is a  logical r**epresentation of a physical network in the cloud**. 

    - It allows we to create a virtual network for resources inside  cloud and gives us complete control over it. we can select our own private IP range, decide on the number of subnets required, configuration of route tables, network gateways etc.

- Why VPC?
    -  a Virtual Private Cloud (VPC) is required in cloud computing to create a **private and isolated network environment** for our resources
    ![justImage](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*ZQff3oaM76UiIDmQ.png)

- concept in VPC?

    2. **Availability Zones (AZs):** AZs are like different sections of our neighborhood. Each section might have its own characteristics (e.g., terrain, facilities), but they're all part of the same neighborhood. In the cloud, AZs are physically separate data centers in different locations.
    3. **Public Subnet and Private Subnet:**
        - **Public Subnet:** Imagine this as the front yard of our house, visible to everyone passing by. we might have our mailbox, a garden, or a porch there. In the cloud, a public subnet is where resources are directly accessible from the internet.
        - **Private Subnet:** This is like the backyard of our house, not visible from the street. we might have a swimming pool, a barbecue area, or a playground there. In the cloud, a private subnet is where resources are not directly accessible from the internet.
    4. **Internet Gateways (IGWs):** An internet gateway is like the main entrance to our neighborhood. It allows traffic to flow in and out of our VPC, connecting our private space to the outside world.
    5. **NAT Gateways:** NAT gateways are like our backyard gatekeepers. They allow resources in our private subnet to access the internet indirectly while keeping them hidden from the outside world.
    6. **Public Route Table and Private Route Table:**
        - **Public Route Table:** Think of this as a map for people visiting our house. It shows them the way to our front yard (public subnet) and the main entrance (internet gateway).
        - **Private Route Table:** This map is for our family and friends who know the secret paths to our backyard (private subnet). It guides them to the backyard gatekeepers (NAT gateways) to access the internet.
    7. **Network Access Control Lists (NACLs):** NACLs are like security guards at the entrances of our neighborhood sections (AZs). They check everyone coming in or going out to make sure they follow the rules. In the cloud, NACLs help control traffic flow in and out of our subnets based on rules we define.
    8. **Security Groups:** Security groups are like security cameras and alarms installed around our house. They monitor who's trying to access our resources (like our front yard or backyard) and only allow trusted visitors inside.
    
    ### Relations between Them:
    
    - our VPC (property) contains multiple availability zones (neighborhood sections).
    - Each availability zone can have public (front yard) and private (backyard) subnets.
    - Public subnets are accessible from the internet via internet gateways.
    - Private subnets access the internet through NAT gateways.
    - Public and private subnets have their own route tables guiding traffic in and out.
    - NACLs act as security guards controlling traffic at the entrance of each subnet.
    - Security groups monitor and control access to our resources within the VPC.
 
 - VPC peering

    AWS VPC Peering connection is a networking connection between two VPCs that enables we to route traffic between them privately. Instances in either VPC can communicate with each other as if they are within the same network.

    ![justImage](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Abu4eeFODEkdG7hXwvb5dg.png)

    - Advantages of VPC peering
        - Low cost since we need to pay only for data transfer.
        - No bandwidth limit.

    - Disadvantages of VPC peering
        - Complex at scale. Each new VPC increases the complexity of the network. Harder to maintain route tables compared to TGW.
        - No transit routing.
        - Maximum 125 peering connections per VPC.
 - Transit Gateway
    
    AWS Transit Gateway is a fully managed service that connects VPCs and On-Premises networks through a central hub without relying on numerous point-to-point connections or Transit VPC.

    we can attach all our hybrid connectivity (VPN and Direct Connect connections) to a single Transit Gateway instance, consolidating and controlling our organization’s entire AWS routing configuration in one place.

    ![justImage](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*kXh27DyJkCv-qdY2z9yNGw.png)

    - Advantages of Transit Gateway
        - Simplified management of VPC connections. Each spoke VPC only needs to connect to the TGW to gain access to other connected VPCs.
        - Supports more VPCs compared to VPC peering.
        - TGW Route Tables per attachment allow for fine-grained routing.
    - Disadvantages of Transit Gateway
        - Additional hop introduces some latency.
        - Extra cost of hourly charge per attachment in addition to data fees.

    - Difference between VPC peering and Transit Gateway

        VPC Peering and Transit Gateway are used to connect multiple VPCs. VPC Peering provides Full-mesh architecture while Transit Gateway provides hub-and-spoke architecture. Transit Gateway gives VPC connectivity at scale and simplifies VPC-to-VPC communication management over VPC Peering with a large number of VPCs.

        Key Differences: VPC Peering vs Transit Gateway

            Connectivity Options
            Peering: VPC to VPC. Hybrid connectivity is not supported.
            TGW: VPC to VPC. Supports hybrid connectivity using VPN or Direct Connect Gateway attachments. Reuse same VPN/DX connection for multiple VPCs.

            Architecture
            Peering: Full Mesh (One to one mapping).
            TGW: Hub and Spoke.

            Transitive Routing
            Peering: Not supported.
            TGW: Supported.

            Network Connectivity
            Peering: Supports Inter-region and Intra-region VPCs connectivity.
            TGW: Supports Inter-region and Intra-region VPCs connectivity.

            Complexity
            Peering: Increases with VPC count. we need to set up a VPC Peering between every VPC. Less complexity with a small number of VPC count.
            TGW: Increases with Transit Gateway count/region count. Less complexity with a higher number of VPC count compares to VPC Peering. we need to manage a very less number of connections/attachments.

            Scale
            Peering: Up to 125 active Peers/VPC.
            TGW: Up to 5,000 Attachments per Region.

            Bandwidth limit
            Peering: No limit.
            TGW: Up to 50 Gbps (burst)/attachment.

            Latency
            Peering: Lowest.
            TGW: Slightly higher compared to VPC Peering because of additional Transit Gateway hop.

            Cost
            Peering: Data transfer. (operational cost is high)
            TGW: Data transfer, Data processing, and Hourly per attachment. (operational cost is less)

            Visibility/Monitoring
            Peering: VPC Flow Logs. Limited visibility compared to TGW.
            TGW: VPC Flow Logs, Transit Gateway Network Manager, CloudWatch Metrics.

            Security group (cross-referencing)
            Peering: Supported.
            TGW: Not supported.

        use cases:
        
            VPC-Peering
                Number of VPCs to be connected is lower (~<10).
                we need multiple VPCs’ connectivity to On-premises.
                we want to minimize data transfer costs when significant volumes of data transfer across regions, VPC Peering is cost-effective.
                Need for low latency.
                we need high throughput. Network bandwidth requirement is more than 50 Gbps.
            
            Transit Gateway
                - we need VPC connectivity at scale. Number of VPCs to be connected is higher (~>10) or scale in the future as the business grows.
                - we need network-level segmentation. (possible with multiple TGW route tables)
                - we need multiple VPCs connectivity to On-premises.
