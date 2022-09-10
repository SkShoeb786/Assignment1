pipeline{
	agent{
		label{
			label'built-in'
			customWorkspace'/mnt/projects/assignment1/22q3'
			}
		}
	stages{
		stage('22q3'){
			steps{
				echo "this is 22q3"
			}
		}
		stage('sync s3'){
			steps{
				sh 'aws s3 rm s3://sk.bucket/assignment1/22q3/*'
				sh 'aws s3 cp /mnt/projects/assignment1/22q3 s3://sk.bucket/assignment1/22q3 --recursive'
			}
		}
		stage('get index.html'){
			agent{
				label{
					label'Slave3'
					}
				}
			steps{
				sh "sudo rm -rf /var/www/html/*"
				sh "sudo aws s3 cp s3://sk.bucket/assignment1/22q3/index.html /var/www/html/"
			}
		}
	}
}
