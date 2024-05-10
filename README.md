# Hosting a Static Website using AWS S3 and CloudFront

A static website is a simple type of website made up of basic files like HTML, CSS, JavaScript, and images. It doesn't have any fancy features like processing data or connecting to databases.

Amazon S3 is a service that gives us a place to store our website files. We can set up a special area in S3 to host our static website so that it's accessible online.

Amazon CloudFront helps our website load faster for people all over the world. It stores copies of our website in different locations, so when someone wants to view it, they can access it quickly, no matter where they are.

To achieve the deployment of a static site using s3 bucket and cloudfront here are the steps:

### STEP 1: Setting up a bucket on Amazon s3

* After logging into the AWS Console, use the search bar to find "S3" before clicking on it.
![s3 service on search bar](images/bucket-creation1.png)

* Click on the "Create Bucket" button to create a new storage bucket.
![s3 bucket creation](images/bucket-creation2.png)

* Enter a bucket name
![s3 bucket naming](images/bucket-config1.png)

* Checkbox for "Block all public access" is  left ticked as we are creating a private bucket.
![s3 bucket private config](images/bucket-config2.png)

* Leaving all other settings as they are, "Create bucket" button at the bottom of the screen is clicked.
![s3 bucket creation](images/bucket-config3.png)


### STEP 2: Upload the website files to the s3 bucket.

* After bucket is successfully created, this page comes up. To view the bucket, click on the bucket name.
![s3 bucket created](images/bucket-created.png)

* Click on upload button to upload files for site to be hosted.
![upload files button clicked](images/upload-files.png)

* Click the "Add Folder" button to upload all files and folders for the  website.
![add folder for website](images/add-files.png)

* Select folder for the website and click on "open".
![select files to upload to bucket](images/select-folder1.png)

* After files are uploaded, scroll to bottom of page and click on "Upload" button.
![upload files](images/select-folder3.png)

* After folder is successfully uploaded to bucket and you are redirected to this page, click on "Close" button to return to bucket details page.
![files successfully uploaded](images/upload-files-success.png)

* To avoid errors when site is being rendered, we will move the contents of the folder to the root of the bucket. Steps to achieve this are as follows:
1. From the "Object" tab on the object details page, the object or uploaded folder is selected.
![select object](images/select-object.png)

2. All contents in the folder are selected. Click on the actions tab and select "move".
![move contents of object](images/move1.png)

3. Click on browse.
![move contents of object](images/move2.png)

4. Select name of bucket.
![move contents of object](images/move3.png)

5. Select "Choose destination"
![move contents of object](images/move4.png)

6. Select move.
![move contents of object](images/move5.png)
### STEP 3: Setting up static website hosting for S3 bucket.

* On the bucket details page, navigate to the "properties" tab, then scroll down to the "static website hosting" section located at the bottom. Click on the "edit" button to proceed.
![static website hosting section](images/static-site-hosting-edit.png)

* Check the "enable" checkbox. In the input field labeled "Index document," enter the name of the default page of the website, which in this case is "index.html."
![static website hosting section](images/static-site-hosting-edit2.png)

* Scroll to the bottom of the page and click on The "Save Changes" button.
![save changes on static website hosting section](images/save-changes.png)

* Once the changes have been successfully saved, a link will be generated as shown below to access the website.
![website link](images/website-link.png)


### STEP 4: Setting up a CloudFront Distribution.

* on the AWS Console, use the search bar to find "cloudfront" before clicking on it.
![cloudfront](images/cloudfront.png)

* Click on "Create a cloudfront distribution"
![cloudfront creation](images/cloudfront2.png)

* Select the name of bucket to be used in the origin field.
![cloudfront configuration](images/cloudfront3.png)

* Tick the "Origin access control settings (recommended)" checkbox and click onn the "Create new OAC" button.
![cloudfront configuration](images/cloudfront4.png)

* Leave all default settings and click on the "Create" button
![Origin access control creation](images/OAC-creation.png)

* Scroll down to the Web Application Firewall section and enable security protections.
 ![cloudfront configuration](images/cloudfront5.png)

 * Scroll further down to the "Default root object" field and input document root of the website.
 ![cloudfront congiguration](images/cloudfront6.png)

 * Scroll to bottom of the page and click on the Create distribution button.
![cloudfront configuration](images/cloudfront7.png)


### STEP 5: Update s3 Bucket Policy.

* After cloudfront diistribution is successfully created, an s3 bucket policy is received which is to be updated. Copy the policy and then click on the redirection link whhich  will take you to the bucket details page.
![bucket policy generated](images//edit-policy.png)

* Navigate to the permissions tab and scroll down to the "Bucket policy" section. 
![edit bucket policy section](images/edit-policy2.png)

* Click on edit and paste the copied bucket policy into the input field. Scroll to the bottom of the page and click on the  "Save changes" button.
![edit bucket policy](images/edit-policy3.png)

* Navigate back to the cloudfront overview page and copy the distribution domain name provided.
![copy dns link](images/copy-dns.png)

* Input link into browser and you should be able to see thw site.
![hosted site](images/site.png)