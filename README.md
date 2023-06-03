# dockerdockergo automatic do it!
Docker image push to Harbor. uploading multiple images from a tar file to a remote registry such as Harbor. Currently, the process involves loading the images from the tar file using docker load, tagging each image with the remote registry URL and project name using docker tag, and then pushing each image to the remote registry using docker push. This process can be time-consuming and cumbersome, especially when dealing with a large number of images.
## need env
 makesure install python3
 ```bash
 python3 -V
 ```
## use - init
```bash
chmod +x dockerdockergo
mv dockerdocker /usr/bin
dockerdockergo -s
# Set up shell completion to autocomplete filenames when using the -f and -R parameters.
```
## use - push a tar file images to harbor repository
```bash
dockerdockergo -h 192.168.200.30 -p k8s -f /root/image.tar
```
- -h your harbor host
- -p your harbor project
- -f your tar file path  



`more tar file?`
```bash
dockerdockergo -f {/root/image1.tar,/root/image2.tar}
```
`The -h option and the -p option, This information will be saved in the /root/.dokerdockergo.json file.`

## use - push all images to harbor repository
```bash
dockerdockergo -A
```
- -A will push all `docker images` image
## future
- -R Replace image names in files in the specified directory  
`now have utf8 issue`
```bash
dockerdockergo -R /root/wokerdir 
```
We first use Harbor's API to get a list of images in the Harbor repository and store them in the harbor_images list. Then, when performing a replace operation, we use the lambda function to check if the matching text exists in the harbor_images list. If it does, the replacement operation is performed; otherwise, the original text is kept.