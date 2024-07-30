pipeline{
	agent any
	
	tools{
		maven 'maven_3.8.8'
	}
	
	stages{
		stage('Checkout'){
			steps{
				echo "checkout stage"
        git 'https://github.com/KusumWakare/travelApp.git'
			}
		}
		
		stage('Test'){
			steps{
			  echo "Running html and css checks"
			}
		}
		
		stage('Build'){
			steps{
			  echo "Building the project....."
			}
		}
		
		stage('Deploy'){
			steps{
			  echo"Deploying to GitHub pages"
        withCredentials([string(credentialsId: 'github-token', variable: 'GITHUB_TOKEN')]) {
                    sh '''
                    git config --global user.email "kusum.wakare99@gmail.com"
                    git config --global user.name "Kusum Wakare"
                    git clone --branch gh-pages https://KusumWakare:${GITHUB_TOKEN}@https://github.com/KusumWakare/travelApp.git gh-pages
                    cp -r * gh-pages/
                    cd gh-pages
                    git add .
                    git commit -m "Deploy to GitHub Pages"
                    git push origin gh-pages
                    '''
			}
		}
	}
}
