## Wat

Uses the great implementation of Simon Braconnier [JODconverter](https://github.com/sbraconnier/jodconverter) to offer LibreOffice as an Document-Converter Web-Service.   

This docker image is a "all you need" and should help you running [JODconverter](https://github.com/sbraconnier/jodconverter) as a WebApp utilizing the packaged LibreOffice for conversions. 
Ultimately this should be your "document conversion chain" service

## Builds info

- Office OpenJDK 10 Java (since that is what we want with docker)
- Debian SID
- using glibc > 1.53 to fix CPU usage of LibreOffice
- LibreOffice is 6.1 right now

Hint: We cannot split [JODconverter](https://github.com/sbraconnier/jodconverter) and LibreOffice into two seperate images since for now, jodconverter has to be running on the same machine as LibreOffice.
The main reason behind this is, that [JODconverter](https://github.com/sbraconnier/jodconverter) does manage the LibreOffice instances itself, starts and stop them. It does not just connect to it (and if, it uses a local socket)

## Run

Thats the variant with a web-GUI (see screenshot)

    docker run --memory 512m --rm -p 8080:8080 eugenmayer/jodconverter:gui
    
Now you can connect to http://localhost:8080 with a nice web-ui for conversion
![Screenshot](https://github.com/EugenMayer/docker-image-jodconverter/blob/master/webapp.png)  

Or you pick the variant a REST interface only only

    docker run --memory 512m  --rm -p 8080:8080 eugenmayer/jodconverter:rest
    
Now go on http://localhost:8080/swagger-ui.html to inspect the available endpoints. Docs under
![Screenshot](https://github.com/EugenMayer/docker-image-jodconverter/blob/master/rest.png)  
 
For more please check the wiki at https://github.com/sbraconnier/jodconverter

## Docker images

- `eugenmayer/jodconverter:gui` - the WebGUI, spring based converter
- `eugenmayer/jodconverter:rest`
- `eugenmayer/jodconverter:base`
  
## Build youerself

    make build
    make start-gui 
    # or
    make start-rest
    
now see above under "Run" how to access it

## Credits

All of those please forward to https://github.com/sbraconnier/jodconverter - he does the real work :) 
And of course also credits to LibreOffice for actually giving us the headless mode and the conversion options in the first place
    
