pipeline {

agent {
			label{
						label 'qa'
						customWorkspace '/mnt/slave/wars'
			}
}

stages{
			stage ('containers-qa'){
								steps{
								            sh "rm -rf *"
											
									     	sh "git clone https://github.com/Mahfooz118/compose-practice.git"
								            sh "sudo yum install docker -y"
											sh "sudo systemctl start docker"
											
											sh "sudo chmod 777 /mnt/slave/wars/compose-practice/compose/docker-compose.yaml"
		                                    sh " sudo cd /mnt/slave/wars/compose-practice/compose"

											sh "docker-compose up -d --scale tomcat=2"
								}
								
			}
			
			stage ('containers-dev'){
			agent {
						label {
									label 'dev'
									customWorkspace '/mnt/slave/wars'
						}
			}
								steps {
										 sh "rm -rf *"
											
									     	sh "git clone https://github.com/Mahfooz118/compose-practice.git"
								            sh "sudo yum install docker -y"
											sh "sudo systemctl start docker"
											sh "sudo chmod 777 /mnt/slave/wars/compose-practice/compose/docker-compose.yaml"
                                            sh " sudo cd /mnt/slave/wars/compose-practice/compose"
											sh "docker-compose up -d --scale tomcat=2"
								}
			}
			
			
}
}
