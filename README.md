# ws-screenshot CI/CD pipeline

<a href="https://dash.elest.io/deploy?source=cicd&social=dockerCompose&url=https://github.com/elestio-examples/ws-screenshot"><img src="deploy-on-elestio.png" alt="Deploy on Elest.io" width="180px" /></a>

Deploy ws-screenshot with CI/CD on Elestio

<img src="ws-screenshot.gif" style='width: 100%;'/>
<br/>
<br/>

# Once deployed ...

You can open ws-screenshot UI here:

    URL: https://[CI_CD_DOMAIN]
    login: "root"
    password: [ADMIN_PASSWORD]

# Usage

## REST API

Make a GET request (or open the url in your browser):

    https://[CI_CD_DOMAIN]/api/screenshot?resX=1280&resY=900&outFormat=jpg&isFullPage=false&url=https://vms2.terasp.net&headers={"foo":"bar"}

## Websocket API

    var event = {
        cmd: "screenshot",
        url: url,
        originalTS: (+new Date()),
        resX: resX,
        resY: resY,
        outFormat: outFormat,
        isFullPage: isFullPage,
        headers: {
            foo: 'bar'
        }
    };

You can check /public/js/client.js and /public/index.html for a sample on how to call the Websocket API

# Supported parameters

- url: full url to screenshot, must start with http:// or https://
- resX: integer value for screen width, default: 1280
- resY: integer value for screen height, default: 900
- outFormat: output format, can be jpg, png or pdf, default: jpg
- isFullPage: true or false, indicate if we should scroll the page and make a full page screenshot, default: false
- waitTime: integer value in milliseconds, indicate max time to wait for page resources to load, default: 100
- headers: add extra headers to the request

# cURL Command for Downloading an Image

To download an image using cURL, you can use the following command:

    curl -u root:[ADMIN_PASSWORD] -o <YOUR/PATH>/<YOUR_FILENAME>.<YOUR_OUTFORMAT> "https://[CI_CD_DOMAIN]/api/screenshot?<YOUR_PARAMETERS>&url=<YOUR_URL>"

For example:

    curl -u root:[ADMIN_PASSWORD] -o /opt/app/google.jpg "https://[CI_CD_DOMAIN]/api/screenshot?resX=1280&resY=900&outFormat=jpg&isFullPage=false&url=https://www.google.com"

Explanation of the parameters:

- `-o <YOUR/PATH>/<YOUR_FILENAME>.<YOUR_OUTFORMAT>`: Specifies the output file path and filename along with the desired output format.

- `"https://[CI_CD_DOMAIN]/api/screenshot?<YOUR_PARAMETERS>&url=<YOUR_URL>"`: Specifies the URL for the screenshot API along with any additional parameters you want to include (replace `<YOUR_PARAMETERS>` and `<YOUR_URL>` with your specific values).

Feel free to adjust the command according to your needs and replace the placeholders with your actual information
