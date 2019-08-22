pipeline
{
	agent any
		stages
		{
			stage('One')
			{
				steps
				{
					echo 'In 1st stage'
				}
			}
			stage('Two')
			{
				steps
				{
					input('do u want to continue from 2nd stage?')
				}
			}
			stage('Three')
			{
				when
				{
					not
					{
						branch "master"
					}
				}
				steps
				{
					echo 'In 3rd stage'
				}
			}
			stage('Four')
			{
				parallel
				{
					stage('Unit Test')
					{
						steps
						{
							echo "In Unit test 4th block"
						}
					}
					stage('Integration test')
					{
						agent
						{
							docker
							{
								reuseNode false
								image 'ubuntu'
							}
						}
						steps
						{
							echo "In Integration test 4th block"
						}
					}
				}	
			}		
		}
}