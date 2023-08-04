# Cloud-Architecture-Case-Study
A case study in which a sample network topology and corresponding documentation must be created for a small and medium size company. Prepared as part of the coursework for ISDS 4130

This course was one of my favorites, and I took a lot of effort and pride in creating this case.

Below can be seen sample diagrams of network topologies, and how they adhere to the AWS Well-Architected Framework!

Small-Scale Business:

<img width="563" alt="image" src="https://github.com/aaltam6/Cloud-Architecture-Case-Study/assets/87050733/b47e883f-c89b-4e17-bc0f-a1c059acdaa6">

Large-Scale Business:

<img width="604" alt="image" src="https://github.com/aaltam6/Cloud-Architecture-Case-Study/assets/87050733/44c03c7c-7e30-44c1-b7d6-5be6023a5298">

Pillar 1: Operational Excellence. The incorporation of CloudWatch for event monitoring, KMS for user credential storage, and a Glacier S3 bucket for routing logs ensure working statistics are easily presented to administrators. These measures will enable more expeditious failure recovery and judicial operations monitoring. 

Pillar 2: Security. All data in transit within our network is encrypted by default since it is within a VPC. CloudFront also ensures data remains protected once it leaves our network and is cached in an edge location. Our network-wide firewall and respective firewall endpoints ensure both inbound and outbound traffic is filtered of harmful content. Cognito ensures user authentication, and CloudWatch monitors all traffic for any signs of danger. Our defense-in-depth is 5 layers deep by the time it reaches our core databasing and adheres to industry standards throughout with a total of 6 layers of defense across total traffic. If desired, data stored within our databasing can remain encrypted with keys stored in our KMS instance, this may be implementable for customer payment or personal information and would push our tally to 7 layers of defense. Anything short of an extremely hardened state actor with extensive computing power would be hard-pressed to mount a notable attack on this architecture.

Pillar 3: Reliability.  Elastic Load Balancing between multiple Availability Zones, optional CloudWatch Alarms, and multiple databasing solutions with read replicas and deep freeze snapshots will ensure absolute reliability in the event of all but the most catastrophic of events. No amount of load can outpace on-demand computing power at the hands of our administrators with AWS’s impressive computing capabilities.

Pillar 4: Cost Optimization. Auto-Scaling functionality and judicial monitoring by our administrators (who are aided by CloudWatch) will ensure we do not overprovision computing power during spikes in demand, and the reservation of reserved instances will keep our baseline computing costs to a minimum. The decision to connect a standby and read replica databases is one that may be slightly more costly but will ensure an extremely robust failure response that will save us more money than it will cost in the long run. The utilization of Simple Queue Service in tandem with the RDS Database will ensure data is not lost in the case of a filled database or of a database at capacity in times of intense load. This saves money as well, as we no longer need to provision our database to a high rate, but instead to an average rate that makes the most of the queue's temporary storage.

Pillar 5: Performance Efficiency. With reserved instances running M7g General Purpose Processors, and the option for nearly unlimited on-demand computing power, it would be difficult to overwhelm our infrastructure by nature of sheer computing load. Elastic Load Balancing and Edge Caching ensure the load is distributed evenly, and in proximity to users, to keep our latency as low as possible for a quick and clean experience.
