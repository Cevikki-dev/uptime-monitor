# Build Log

## Day 2: First EC2 instance

- Launched t3.micro, Ubuntu 26.04 LTS in eu-north-1, tagged Project=uptime-monitor, IMDSv2 required.
- Failure 1: SSH timed out. Cause: my ISP changed my public IP, so the /32 rule no longer matched. Fix: set the rule source to My IP again. Lesson: a timeout means the firewall dropped the packets.
- Failure 2: "Identity file not accessible". Cause: ran SSH from the wrong folder. Fix: cd to the folder with the key.
- Failure 3: the SSH rule became Custom TCP port 0. Cause: edited the rule wrongly. Fix: set Type to SSH, port 22.
- Verified: a metadata request without a token returned 401, and with a token it returned the instance ID.
