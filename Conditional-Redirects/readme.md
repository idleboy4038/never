# Conditional redirects

Conditional redirects allow you to redirect users based on specific conditions or rules. Here are a few examples of conditional redirects:

1. Geolocation Redirect:
   - Redirect users based on their geographic location. This can be useful for serving region-specific content or directing users to country-specific versions of your website.

   ```javascript
   if (navigator.geolocation) {
     navigator.geolocation.getCurrentPosition(function(position) {
       var latitude = position.coords.latitude;
       var longitude = position.coords.longitude;

       if (latitude > 40 && longitude < -70) {
         window.location.href = "https://example.com/us";
       } else {
         window.location.href = "https://example.com/international";
       }
     });
   }
   ```

   In the example above, if the user's latitude is greater than 40 and longitude is less than -70 (representing a location in the United States), they will be redirected to `https://example.com/us`. Otherwise, they will be redirected to `https://example.com/international`.

2. Device Type Redirect:
   - Redirect users based on the type of device they are using, such as desktop, tablet, or mobile. This can be helpful for optimizing the user experience for different device types.

   ```javascript
   var userAgent = navigator.userAgent.toLowerCase();

   if (userAgent.includes("mobile")) {
     window.location.href = "https://example.com/mobile";
   } else if (userAgent.includes("tablet")) {
     window.location.href = "https://example.com/tablet";
   } else {
     window.location.href = "https://example.com/desktop";
   }
   ```

   In this example, if the user is accessing the site from a mobile device, they will be redirected to `https://example.com/mobile`. If it's a tablet, they will be redirected to `https://example.com/tablet`. Otherwise, for desktop devices, they will be redirected to `https://example.com/desktop`.

3. Referring URL Redirect:
   - Redirect users based on the URL they came from. This can be useful for directing users who land on specific pages from external sources to relevant content on your website.

   ```javascript
   var referringURL = document.referrer;

   if (referringURL.includes("google.com")) {
     window.location.href = "https://example.com/from-google";
   } else if (referringURL.includes("facebook.com")) {
     window.location.href = "https://example.com/from-facebook";
   } else {
     window.location.href = "https://example.com/default";
   }
   ```

   In this example, if the user arrived at the website from Google, they will be redirected to `https://example.com/from-google`. If they came from Facebook, they will be redirected to `https://example.com/from-facebook`. Otherwise, for other referring URLs, they will be redirected to the default URL `https://example.com/default`.

These are just a few examples of conditional redirects. You can customize and combine conditions based on your specific requirements and the information available to you.
