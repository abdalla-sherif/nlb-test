# Network Load Balancer Setup (NLB) with Two EC2 Instances
# --------------------------------------------------------

## Description
# This setup demonstrates how I created a Network Load Balancer on AWS,
# attached a Target Group to it, and added two EC2 instances — each running
# a different User Data script. The goal is to test how the NLB distributes
# traffic between the two instances through port 3000.

# --------------------------------------------------------
## 1. Create Network Load Balancer
# - Created a Network Load Balancer (Layer 4 - TCP).
# - Configured it to listen on port 3000.
# - The NLB forwards all traffic to the registered Target Group.

# --------------------------------------------------------
## 2. Create Target Group
# - Created a Target Group using protocol TCP on port 3000.
# - Registered *two EC2 instances* inside the Target Group.
# - Each instance uses different User Data so we can see different outputs
#   when the NLB distributes traffic.

# --------------------------------------------------------
## 3. EC2 Instances Configuration
# - Each EC2 instance was launched with unique User Data script.
# - User Data example structure:
#
#   #!/bin/bash
#   # Start a simple HTTP/TCP server on port 3000
#   echo "اHello from EC2 Web Application-test2" > /var/www/html/index.html
#
# - The script differs between Instance 1 and Instance 2.
# - Both instances listen on port 3000.

# --------------------------------------------------------
## 4. Associate Target Group with NLB
# - Attached the Target Group to the NLB Listener on port 3000.
# - Now the NLB routes traffic to both instances using TCP forwarding.

# --------------------------------------------------------
## 5. Security Group Configuration
# - Created a Security Group and attached it to both EC2 instances.
# - Added an inbound rule:
#     • Port: 3000
#     • Source: My Public IP
# - This allows me to test the application from my browser.

# --------------------------------------------------------
## 6. Testing the Network Load Balancer
# - After everything was created, I opened the NLB DNS name in the browser.
# - Since each instance has a different User Data script,
#   each refresh shows output from different instances.
#
#   Example:
#     Refresh 1 → "Hello from EC2 Web Application-test2"
#     Refresh 2 → "hello sir"
#
# - This confirms the NLB is correctly distributing traffic.

# --------------------------------------------------------
## Summary
# - NLB created successfully.
# - Target Group created and attached.
# - Two EC2 instances registered with different User Data.
# - Security Group configured to allow traffic on port 3000.
# - NLB traffic distribution verified.


