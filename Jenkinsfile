pipeline{
	agent{
		label{
			label'built-in'
			customWorkspace'/mnt/projects/assignment1/22q1'
			}
		}
	stages{
		stage('22q1'){
			steps{
				echo "this is 22q1"
			}
		}
		stage('sync s3'){
			steps{
				sh 'aws s3 rm s3://sk.bucket/assignment1'
				sh 'aws s3 sync /mnt/projects/* s3://sk.bucket/'
			}
		}
		stage('get index.html'){
			agent{
				label{
					label'Slave1'
					}
				}
			steps{
				sh "sudo rm -rf /var/www/html/*"
				sh "sudo aws s3 cp s3://sk.bucket/assignment1/22q1/index.html /var/www/html/"
			}
		}
	}
}
