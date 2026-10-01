pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo "Build Docker Image"
                bat "docker build -t mypythonflaskapp ."
            }
        }
        stage('Run'){
            steps{
                echo 'Run application in Docker Container'
                bat "docker rm -f mycontainer || exit 0"
                //forcibly remoces the Dcoker container if it is already running
                //If the container doesn't exist, this command will fail, so we use '|| exit 0' to ignore the error,and exit with success status.
                //If exit 0 is not used, the pipeline will fail and stop executing the next steps.
                bat "docker run -d -p 5000:5000 mypythonflaskapp"
                //The -d flag runs the container in detached mode, allowing it to run in the background while the pipeline continues executing.
            }
            
        }
    }
}