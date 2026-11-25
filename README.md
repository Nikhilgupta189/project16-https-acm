# Project 16: Enable HTTPS Using AWS ACM

## Objective
Configure HTTPS access using AWS Certificate Manager and an Application Load Balancer, while blocking HTTP connections.

## Technologies Used
- AWS Certificate Manager (ACM)
- AWS Application Load Balancer
- Amazon EC2
- AWS CLI
- OpenSSL
- Ubuntu Linux

## Implementation
1. Reused the existing Project 20 Application Load Balancer.
2. Generated a self-signed SSL/TLS certificate using OpenSSL.
3. Imported the certificate into AWS Certificate Manager.
4. Configured the ALB security group to allow HTTPS on port 443.
5. Created an HTTPS listener using the imported ACM certificate.
6. Forwarded HTTPS requests to the existing EC2 target group.
7. Verified the HTTPS endpoint using `curl -k`.
8. Removed the HTTP listener on port 80.
9. Blocked HTTP traffic in the ALB security group.
10. Verified that HTTP connections failed while HTTPS remained functional.

## Verification
- HTTPS listener successfully configured.
- HTTPS request returned HTTP/2 200.
- Nginx webpage accessed through HTTPS.
- HTTP access blocked.

## Certificate Limitation
A self-signed certificate was used for this training demonstration. The HTTPS test used `curl -k`, which bypasses certificate verification. Browser-trusted HTTPS and hostname validation were not demonstrated.

## Screenshots
1. `01-acm-certificate.png`
2. `02-https-listener.png`
3. `03-https-working.png`
4. `04-http-blocked.png`

## Conclusion
Successfully demonstrated TLS-enabled connectivity through an AWS Application Load Balancer using an imported ACM certificate and blocked unencrypted HTTP access.
