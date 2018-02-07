* Build a docker file and tag it as sample:v1
  ```
  docker build -t sample:v1 .
  ```
  
 * Run as daemon and map interal port 5000 to external port 5001:
   ```
   docker run -d -p 5000:5000 sample:v1
   ```
   
 * Stop container
    ```
    docker container ls
    docker container stop <cont_id>
    ```
 
