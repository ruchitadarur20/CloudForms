Author: RUCHITA DARUR <br>
Date: 2/7/2025 <br>
Course: SWE 645 <br>
Assignment: Assignment 1 <br>

Part-A<br><b>Deployment Links:-</b> <br>assignmentparta (S3):- http://assissment1.s3-website-us-east-1.amazonaws.com/

EC2 Survey Form:-http://3.145.199.187/student_form.html


## 1. Overview
Creating and hosting a class site using Amazon S3 is explained in detail in this paper. An picture, a text, and an error page will all be included on the static homepage. An S3 bucket URL will be used to make the website publicly available.

## 2. Requirements
* An AWS Account.<br>
* Basic knowledge of HTML and CSS.<br>
* Internet access for AWS setup.

## 3. Steps to Host the Homepage on S3
Step 1: Create the Website Files:-<br>
- Create a new folder named as assissment1.<br>
- Inside this folder, <br>
	- index.html (Main Homepage)<br>
	- error.html (Error Page)
- Use a W3.CSS template or any CSS framework to style your homepage.
- Ensure the index.html contains:<br>
	- A heading with the class name.<br>
	- A short paragraph describing the class.<br>
	- An image (hosted locally or externally).

Step 2: Create an S3 Bucket:-
1.	Log in to AWS Console → Navigate to S3.
2.	Click Create Bucket.
3.	Enter a unique bucket name assissment.
4.	Choose a region (e.g., us-east-1).
5.	Uncheck "Block all public access" (this is required for public access).
6.	Confirm the settings and click Create Bucket.

Step 3: Enable Static Website Hosting:-
1.	Open the S3 bucket you created.
2.	Go to the Properties tab.
3.	Scroll down to Static website hosting and click Edit.
4.	Select "Use this bucket to host a website".
5.	Set index.html as the index document.
6.	Set error.html as the error document.
7.	Click Save Changes.

Step 4: Upload the Website Files:-
1.	Go to the Objects tab in your S3 bucket.
2.	Click Upload → Select index.html and error.html.
3.	Click Upload.

Step 5: Set Public Permissions:-
1.	Navigate to the Permissions tab of the S3 bucket.
2.	Click Bucket Policy.
3.	Paste the following JSON policy (replace     BUCKET_NAME with your actual bucket name):<br>
	
![Getting Started](./assets/Bucket%20Policy.jpg)

4.	Click Save Changes.

Step 6: Retrieve and Test Your Website URL:-
1.	Go to the Properties tab in your S3 bucket.
2.	Scroll down to Static website hosting.
3.	Copy the Endpoint URL (e.g., http://your-bucket-name.s3-website-us-east-1.amazonaws.com).
4.	Open this URL in your browser to verify the homepage is working.
5.	Test an invalid URL to check if the error page is displayed.

## 4.Steps to Deploy the Student Survey Form on EC2
Step 1: Launch an EC2 Instance
1. Go to AWS Console → EC2 Dashboard.
2. Click Launch Instance.
3. Choose Ubuntu as the OS.
4. Select instance type (e.g., t2.micro - free tier).
5. Configure security group (Allow HTTP (port 80) and SSH (port 22)).
6. Click Launch. 

Step 2: Connect to the EC2 Instance
- Use SSH to connect: ssh -i your-key.pem ubuntu@your-ec2-instance-ip

Step 3: Install a Web Server<br>
sudo apt update<br>
sudo apt install apache2 -y

Step 4: Upload Survey Files
1. Use SCP or SFTP to upload survey.html and related files.
2. Move the files to /var/www/html/.
sudo mv survey.html /var/www/html/

Step 5: Test and Access Your Survey Form
- Open a browser and enter:
http://your-ec2-instance-ip/survey.html

## 4. Linking EC2 Application to S3 Homepage:-
- Modify index.html on S3 to include a link to the EC2-hosted survey form. Example:
<a href="http://your-ec2-instance-ip/survey.html">Student Survey Form</a>


## 5. Submission Details

Provide the URLs for:

S3 Homepage: http://assignmentparta.s3-website.us-east-2.amazonaws.com/

EC2 Survey Form: http://3.145.199.187/student_form.html

Zip file: assets



