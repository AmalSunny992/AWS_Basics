# HandsOn : Using Amazon LightSail Launch a website with Load Balancer

Setting up two web servers, connecting them to a load balancer on Amazon Lightsail, and pointing them to a domain involves several steps. 
Here's a detailed guide to help you through the process:

## 1. Set Up Two Web Servers on Amazon Lightsail

**Step 1**: Create Two Lightsail Instances

1. Log in to your AWS Management Console.
2. Navigate to Lightsail.
3. Create an instance:
    - Choose the region where you want your instance to be located.
    - Select a blueprint (OS or application). For a web server, you can choose Linux/Unix and then select the appropriate app or stack (e.g., LAMP, Nginx).
    - Choose an instance plan based on your needs.
    - Name your instance (e.g., webserver-1).
    - Create the instance.
4. Repeat the process for the second instance (e.g., webserver-2).

**Step 2**: Configure Your Web Servers
    - Connect to each instance via SSH from the Lightsail console.
    - Set up your web server (e.g., Apache or Nginx) and deploy your application or website on both instances. Ensure both servers serve the same content.

## 2. Set Up a Load Balancer on Lightsail

**Step 1**: Create a Load Balancer

1. In the Lightsail console, go to the Networking tab.
2. Create a load balancer:
    - Name your load balancer (e.g., my-load-balancer).
    - Choose the region where your instances are located.
    - Create the load balancer.

**Step 2**: Attach Instances to the Load Balancer

1. After the load balancer is created, go to its management page.

2. Attach your instances (webserver-1 and webserver-2) to the load balancer.

## 3. Configure SSL/TLS Certificate for the Load Balancer

**Step 1**: Request an SSL/TLS Certificate
1. In the Lightsail console, navigate to your load balancer's management page.
2. Click on the "Certificates" tab.
3. Request a new certificate:
    - Enter your domain name.
    - Add any additional domain names if needed (e.g., www.yourdomain.com).

**Step 2**: Validate the Domain
1. Follow the instructions to validate your domain. This typically involves adding a CNAME record to your domain's DNS settings.
2. Log in to your domain registrar's account and navigate to the DNS settings.
3. Add the CNAME record provided by Lightsail to your DNS settings.
4. Wait for the validation to complete. This may take some time depending on your DNS provider.

**Step 3**: Attach the Certificate to the Load Balancer
1. Once the certificate is issued, return to the load balancer's management page.
2. In the "Certificates" tab, select the issued certificate and attach it to the load balancer.

## 4. Point Your Domain to the Load Balancer

**Step 1**: Get the DNS Name of the Load Balancer
1. In the Lightsail console, navigate to your load balancer's management page.
2. Copy the DNS name of the load balancer.

**Step 2**: Update Your Domain's DNS Settings
1. Log in to your domain registrar's account (e.g., GoDaddy, Namecheap).
2. Find the DNS settings for your domain.
3. Create an A record:
    - Name: @ (or leave it blank, depending on your registrar).
    - Value: Paste the DNS name of your Lightsail load balancer.
    - TTL: Set an appropriate value (e.g., 300 seconds).
    - Save the changes.

## 5. Test Your Setup
1. Wait for DNS propagation (this can take a few minutes to 48 hours).
2. Open your web browser and navigate to your domain.
3. Verify that your website is accessible and that the load balancer is distributing traffic between your two instances.
4. Ensure the site is accessible over HTTPS and that the SSL certificate is properly configured
