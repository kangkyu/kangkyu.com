# kangkyu.com

1. Move all the HTML and CSS files to an S3 bucket
2. Setup "Static website hosting" in "Properties"
3. In "Permissions", do not block public access and allow "s3:GetObject" in the bucket policy
4. Go to ACM (Certificate Manager) and request a certificate - select "DNS Validation" 
5. Add a domain `"www.kangkyu.com"` and get CNAME name and CNAME value
6. Use those two values and setup DNS of `"kangkyu.com"` domain in the registrar website - see https://stackoverflow.com/a/51208517/3622415
7. Wait the certificate to get issued
8. Make a Cloudfront distribution, use the bucket website endpoint from 2 as "Origin domain"
9. And set "Alternate domain name" as `"www.kangkyu.com"` and select "Custom SSL certificate" from 8
10. Go back to domain DNS setting, add as a CNAME record with "www" and the value from Cloudfront ("Distribution domain name")
