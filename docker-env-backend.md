
# RCA: Failure to connect to the backend and MySQL

## Presenting Issue:
Students were unable to connect the frontend to the backend and not connecting to the MySQL database locally or through docker.

## Investigation & Troubleshooting Steps:
* Verified the env files were written correctly.
* Verified Nginx setup and configuration.
* Verified a fix with the axios.js file.
* Confirmed the correct port usage.
* The console confirms a system error 500 and shows that it does not connect to the designated port from the env and defaults to the port 3001.
* **Diagnosis:** Unknown, but speculation is an issue with creating the database connection which causes the env files not to be read and the tables not populating correctly.
* **Initial Attempt to Fix:** Tried to locally connect to the backend, same error. Attempted to alter code and discovered it would not connect to the backend at all. We eventually altered the code to connect to the backend once again.
* **Secondary Failure:** We connected to the backend but it would not connect to the MySQL database to create and populate the tables.
* **Root Cause Speculation:** There might be an error in the docker file that is skipping the step to connect the MySQL database through the backend causing the tables to not exist.

## Mitigation:
Testing docker locally and through the VM. Having alternative steps to connect to the backend without docker, to narrow down steps for debugging.

## Corrective Actions:
* **Updated Axious.js:**
    * **Updated Process.env:** Updated baseURL since it was using process.env instead of import.meta.env.
* **Updated Dockerfile:** It was not correctly reading the values of the env files. Updated the file to read the env information.
