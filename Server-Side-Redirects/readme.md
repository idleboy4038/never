# HTPTS redirects on server-side & client-side

## Server-Side

> HTTP redirects are commonly used to redirect users to a different URL on a website. Here's how you can use different HTTP status codes to implement redirects

1. 301 Redirect (Permanent Redirect):
   - In this type of redirect, you indicate that the requested URL has permanently moved to a new location.

   If you're using an Apache server, you can use the following code in your `.htaccess` file:

   ```apache
   Redirect 301 /old-url https://example.com/new-url
   ```

   If you're using an Nginx server, you can use the following code in your server configuration:

   ```nginx
   server {
     ...
     location /old-url {
       return 301 https://example.com/new-url;
     }
     ...
   }
   ```

   In both cases, when a user visits `https://yourwebsite.com/old-url`, they will be redirected to `https://example.com/new-url`.

2. 302 Redirect (Temporary Redirect):
   - In this type of redirect, you indicate that the requested URL has temporarily moved to a new location.

   The implementation for a 302 redirect is similar to that of a 301 redirect. However, instead of using the code `301`, you use `302` in your redirect configuration.

   For Apache:

   ```apache
   Redirect 302 /old-url https://example.com/new-url
   ```

   For Nginx:

   ```nginx
   server {
     ...
     location /old-url {
       return 302 https://example.com/new-url;
     }
     ...
   }
   ```

   This will temporarily redirect users who visit `https://yourwebsite.com/old-url` to `https://example.com/new-url`.

Remember to replace `https://example.com/new-url` with the actual URL you want to redirect to, and `https://yourwebsite.com/old-url` with the old URL you want to redirect from. Also, ensure that you have appropriate access and permissions to modify server configurations or `.htaccess` files.

HTTP redirects are often used for SEO purposes, ensuring that users and search engines are directed to the correct and updated URLs.

## Client-Side

> Yes, you can set up HTTPS redirects on a GitHub Pages website. GitHub Pages supports HTTPS by default, and you can configure redirects using the Jekyll static site generator or by utilizing client-side JavaScript

Here are two different methods you can use to set up HTTPS redirects on a GitHub Pages site:

1. Jekyll `_config.yml` Method:
   - If your GitHub Pages site uses Jekyll, you can utilize the `_config.yml` file to set up redirects.

   ```yaml
   gems:
     - jekyll-redirect-from

   plugins:
     - jekyll-redirect-from

   redirects:
     - from: /old-url
       to: /new-url
   ```

   In the example above, the `jekyll-redirect-from` plugin is added to the `gems` and `plugins` sections of the `_config.yml` file. Then, the `redirects` section specifies the old URL (`/old-url`) and the corresponding new URL (`/new-url`). When someone visits the old URL, they will be automatically redirected to the new URL.

   After making these changes, you need to rebuild your site using Jekyll and deploy the updated version to GitHub Pages.

2. Client-Side JavaScript Method:
   - If your GitHub Pages site is a static HTML site or doesn't use Jekyll, you can use client-side JavaScript to handle the redirect.

   Add the following JavaScript code to the `<head>` section of your HTML file:

   ```html
   <script>
     if (location.protocol !== "https:") {
       location.href = "https://" + location.hostname + location.pathname + location.search;
     }
   </script>
   ```

   This JavaScript code checks if the current protocol is not HTTPS. If it's not, it constructs the HTTPS URL using `location.hostname`, `location.pathname`, and `location.search`, and then redirects the user to the HTTPS version of the page.

   Save the HTML file, commit it to your GitHub repository, and GitHub Pages will serve the page with the HTTPS redirect in place.

Remember to replace `/old-url` and `/new-url` with the appropriate URLs you want to redirect from and to, respectively.

Please note that when using client-side JavaScript redirects, the initial page load will still use HTTP before the JavaScript code executes and triggers the redirect.
