# Deployment of a Static Website Using AWS S3, and CloudFront

This project outlines the steps to set up a static website using AWS services. We'll use S3 to host website files, set a public read policy on a private bucket, and deliver content globally via CloudFront. This guide is aimed at demonstrating a straightforward method for secure and efficient website deployment on AWS.


## Creating and Configuring the S3 Bucket

After logging into my AWS account, I headed straight to the S3 service by searching for "S3" in the console's search bar. I needed to create a new bucket for my static website, so I clicked on "Create bucket." I named this bucket `**olayinka-altschool-assignment1**`.

![](https://paper-attachments.dropboxusercontent.com/s_616DF3267F57457AECBC75C19DB6C79BD8C52F1F010502590AB89EBCA3BD9FC8_1715375282388_S3+Bucket.png)


Once the bucket was set up, I clicked on its name to access it. Here, I found the option to upload files. I clicked on "Upload" and selected the static files for my website—HTML, CSS, JavaScript, and any images I planned to use. After confirming all files were ready, I clicked "Upload" to move everything to the root directory of my new S3 bucket.

![](https://paper-attachments.dropboxusercontent.com/s_616DF3267F57457AECBC75C19DB6C79BD8C52F1F010502590AB89EBCA3BD9FC8_1715375511195_Document+Upload.png)


 
Once my files were uploaded, the next step was to make them accessible as a website. To do this, I navigated to the **Permissions** tab of my bucket, `**olayinka-altschool-assignment1**`. Here, I found the option for **Static website hosting**. I clicked on it to configure the settings needed to serve my static content.
I enabled static website hosting by selecting the option "Use this bucket to host a website." In the text boxes provided, I entered the name of my index document which is  `**index.html**` and error document. After filling in these details, I saved the settings.

![](https://paper-attachments.dropboxusercontent.com/s_616DF3267F57457AECBC75C19DB6C79BD8C52F1F010502590AB89EBCA3BD9FC8_1715375796002_Enable+Static+Hosting.png)



## Setting Up AWS CloudFront

After configuring my S3 bucket to host the static website, I moved on to setting up AWS CloudFront to distribute the content globally. First, I navigated to the CloudFront service by searching for "CloudFront" in the AWS Management Console.

![](https://paper-attachments.dropboxusercontent.com/s_616DF3267F57457AECBC75C19DB6C79BD8C52F1F010502590AB89EBCA3BD9FC8_1715377274626_Screenshot+2024-05-10+195428.png)


I initiated the creation of a new distribution by clicking on **Create distribution**. For the origin domain, I selected my S3 bucket URL from the dropdown, which was `**olayinka-altschool-assignment1.s3.us-east-1.amazonaws.com**`. In setting up the origin access, I chose the **Origin access control settings**. I clicked on **Create new OAC**, and a pop-up appeared where I verified that my origin name was correctly showing. I left all other settings default and proceeded to create the OAC.

![](https://paper-attachments.dropboxusercontent.com/s_616DF3267F57457AECBC75C19DB6C79BD8C52F1F010502590AB89EBCA3BD9FC8_1715377424718_OAC.png)

![](https://paper-attachments.dropboxusercontent.com/s_616DF3267F57457AECBC75C19DB6C79BD8C52F1F010502590AB89EBCA3BD9FC8_1715377441159_CloudFront.png)


Continuing with the configuration, I scrolled down to the distribution settings and set the **Default root object** to `**index.html**`, ensuring that CloudFront serves the `**index.html**` file when accessing the root URL of the distribution.
Upon clicking **Create distribution**, CloudFront began to deploy, and it automatically generated a new policy for the S3 bucket. I copied this policy and went back to my S3 bucket settings to update the policy accordingly. This ensures that the permissions are correctly set to allow CloudFront to access the S3 bucket.

![](https://paper-attachments.dropboxusercontent.com/s_616DF3267F57457AECBC75C19DB6C79BD8C52F1F010502590AB89EBCA3BD9FC8_1715377589468_S3Policy.png)


Returning to the CloudFront page, I accessed my newly created distribution and noted the **Distribution domain name**, which was `**https://drio36e2ayt0q.cloudfront.net**`. I tested this URL in my browser, and to my satisfaction, my website was successfully deployed and displayed as expected.

![](https://paper-attachments.dropboxusercontent.com/s_616DF3267F57457AECBC75C19DB6C79BD8C52F1F010502590AB89EBCA3BD9FC8_1715377575363_cloudfront.net.png)


The ability to host static content in an S3 bucket and distribute it via CloudFront mirrors real-world applications where businesses need to deliver their content efficiently and at scale. This approach reduces server load, decreases response times, and enhances user experience, making it a preferred method for deploying static websites and web applications.

