## AZURE VIRTUAL SECURITY GROUP SETUP/CONFIGURATION
# Project Overview
This project involves setting up a secure cloud network environment using Microsoft Azure. The primary goals were to create a virtual network (VNet) and implement robust security measures through Network Security Groups (NSGs). This setup ensures that all resources within the cloud environment are secure, scalable, and well-organized.

## Implementing Network Security Groups (NSGs)
After setting up the VNet, I moved on to implementing security measures by configuring a Network Security Group (NSG) for SatiahCorp. An NSG acts as a virtual firewall, allowing me to control inbound and outbound traffic to and from the network. This step was critical for ensuring that the VNet is not only functional but also secure against unauthorized access and potential threats.

# Detailed Setup Process:
# Creating the NSG:

I began by navigating to the Azure portal and searching for "Network security groups." From there, I created a new NSG and assigned it to the resource group I had set up earlier. It was essential to ensure that the NSG was created in the same region as the other resources to maintain consistency and optimize network performance.

![image](https://github.com/user-attachments/assets/a159a965-3e4e-4197-b31c-9e2e9b5462df)

![NSG1](https://github.com/user-attachments/assets/35d8ea72-2503-4c26-b3c5-ec34581d1272)

![NSG2](https://github.com/user-attachments/assets/d649b5e8-7e23-4b40-8f7f-ee84df412f45)

![NSG3](https://github.com/user-attachments/assets/b261ba91-0581-4608-a27c-67a4513136f3)


## Configuring Inbound Rules:

Once the NSG was created, I proceeded to configure inbound security rules, which dictate how incoming traffic is handled. The goal was to create a rule that blocks all inbound traffic by default, thereby securing the network from unauthorized access.

Source: I set the source to "Any," meaning the rule applies to traffic from any origin. This broad scope ensures that no external traffic can reach the resources unless explicitly allowed.

Source Port Ranges: I left the source port ranges as the wildcard (*) to cover all possible ports. Since source ports are often randomly assigned, this setting is crucial to ensure that the rule applies universally, regardless of the specific port used by incoming traffic.

Destination: Similar to the source, I set the destination to "Any," meaning the rule would apply to all destination addresses within the VNet.

Service and Destination Port Ranges: I kept the service setting at "Custom" and used the wildcard (*) for destination port ranges. This combination effectively blocks all incoming traffic, regardless of the service or port being targeted.

Protocol: To ensure comprehensive coverage, I set the protocol to "Any." This choice guarantees that all traffic, whether it's TCP, UDP, or any other protocol, is blocked unless explicitly allowed by another rule.

Action: I selected "Block" as the action for this rule, which prevents all traffic that matches the rule’s criteria from reaching the network.

Priority: Priority is a critical setting in NSGs, as it determines the order in which rules are applied. I set this rule’s priority to 4096, the highest number Azure allows, making it the last rule to be applied. This means that it will block any traffic that hasn't been allowed by a higher-priority rule, serving as a catch-all safety net.

Naming and Description: I named the rule "Default-Deny" and provided a clear description: "Deny all inbound traffic." This descriptive naming convention helps in quickly identifying the rule’s purpose when managing the NSG in the future.

c. Verifying the NSG:

After configuring and saving the inbound rule, I reviewed the NSG’s settings to ensure everything was correctly implemented. The NSG overview provided a summary of the applied rules, confirming that the "Default-Deny" rule was active and that all inbound traffic was effectively blocked.

Strategic Considerations:
The decision to implement a "Default-Deny" rule as the last rule in the NSG is a best practice in network security. This approach ensures that no traffic can reach the network unless explicitly permitted by other rules. It’s a proactive measure that significantly reduces the risk of unauthorized access and potential breaches.

Additionally, by configuring the NSG within the same region as the VNet and resource group, I maintained consistency across the cloud environment. This consistency is vital for performance optimization, as it reduces latency and ensures that all resources operate within the same geographical and technical context.

Conclusion of Security Implementation:
With the NSG in place, I have added a robust layer of security to the VNet, protecting the cloud environment from unauthorized access and potential threats. This setup ensures that the network is not only functional but also secure, laying a strong foundation for future deployments and operations.
