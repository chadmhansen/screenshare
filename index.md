<!DOCTYPE html>
<html lang="en">
  <head>
  </head>
  <body onload="onloaded()">
        <div id="before">
            Branding content goes here.<br/>
            This is on the customer's own web site.<br/>
            The form is an embedded iframe that's coming from ININ.<br/>
        </div>
        <div id="screenshareContainer"></div>
        <div id="after">
            Content of customer's website below iframe/form<br />
            Content of customer's website below iframe/form<br />
            Content of customer's website below iframe/form<br />
        </div>


<script src="https://apps.mypurecloud.com/webchat/jsapi-v1.js" type="text/javascript"></script>

<script type="text/javascript">

        var config = {
            // Webchat service URL
            "webchatServiceUrl": "https://realtime.mypurecloud.com:443",

            //Webchat app URL
            "webchatAppUrl": "https://apps.mypurecloud.com/webchat",

            // Numeric organization ID
            "orgId": 16412,

            // String organization ID
            "orgName": "bughuntprod",

            // Log level (DEBUG, INFO, WARN, ERROR, or FATAL)
            "logLevel": "DEBUG",

            // Locale code of end-user which will be used to localize the widget
            "locale": "en",

            "orgGuid": "82a93788-03da-4575-8be0-a0e1c611f125",

            // CSS class if widget is rendered as frame
            "cssClass": "screenshare-frame",

            // Additional CSS properties if widget is rendered as an iframe.
            // These properties apply to the iframe itself, not to its content.
            "css": {
                "width": "480px",
                "height": "282px",
                "border": "none"
            },

            // The URL of a CSS file to apply to the content of the iframe.
            "contentCssUrl": "screenshare.css",

            //Some customers may use an external application and browser support will not prohibit the initiation of screen share in that case
            "standAloneApplication": false,

            "webchatDeploymentKey": "a31fb79d-f475-40b2-956f-40dfc1bdc132"

        };

        function onloaded() {
            ININ.screenshare.create(config, function(err, screenshare) {
                if (err) {
                    // You should change this block to properly handle errors.
                    console.error(err);
                    if (err.name === 'UNSUPPORTED_BROWSER') {
                        // Redirect to instructions for unsupported browser, or handle appropriately
                        alert('Sorry, either your browser is not supported, or the page is not being served over TLS (HTTPS).');
                        return;
                    }
                    alert('An error occurred launching the screen share widget. See console for details');
                }

            screenshare.renderScreenShareForm({
                containerEl: 'screenshareContainer'
            });
          });
        }
    </script>
  </body>
  </html>
