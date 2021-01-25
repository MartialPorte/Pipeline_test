node {
    checkout scm
    /*
     * In order to communicate with the MySQL server, this Pipeline explicitly
     * maps the port (`3306`) to a known port on the host machine.
     */
    docker.image('martialpre/jenkins_slave_tu:1.3').withRun('-p 22:22') { c ->
	/* Wait until mysql service is up */
	sh 'while !  curl tcp://172.30.11.246:4243 --silent; do sleep 1; done'
	/* Run some tests which require MySQL */
	sh 'cmake --version'
   }
}
