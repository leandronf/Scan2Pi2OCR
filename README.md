# Scan2Pi2OCR
This Project aims to have a RASPI as Saned-Scan-Engine and send the scanned documents to a second more powerfull computer for OCR and potential send to cloud.

```console
sudo apt-get install imagemagick bc exactimage pdftk \
   tesseract-ocr tesseract-ocr-deu tesseract-ocr-eng
```

For use of Buttons is used [insaned](https://github.com/abusenius/insaned)


The Process is to be as followed:
insaned on the RASPi is calling the script scan.sh from the raspi folder.
Please adapt path in file insaned/events/scan and make it executable. 
To enable more scans this script creates a new process for the ocr-task calling ocrit.sh with &.

ocrit.sh manages to transfer the data to the target scanning device - and starts the final OCR-Process there with a ssh execution call.

With this version - supported is the use of tesseract and abby-cloud. 
Abby has really good ocr-capabilities (but payed and with price-politics only good for big count of pages recognition) - still better (at least in German) than tesseract; but [tesseract4](https://github.com/tesseract-ocr/tesseract) with LTSM and (_important_) use of the -l language parameter is really good as well.

The last changes reflect the switch to use docker with tesseract 4. Base of this docker image is [tesseract-ocr-re](https://github.com/tesseract-shadow/tesseract-ocr-re) some changes are in the docker directory. 

