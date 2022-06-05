pipeline
{
  environment
  {
    registry= "rajjakapure/demoimage"
    registryCredential= 'dockerid'
    dockerimage= ''
  }
  agent any
  
  stages
  {
    stage('Build image')
    {
      steps
      {
        script
        {
          dockerImage=docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy the image')
    {
      steps
      {
        script
        {
          docker.withRegistry( '',registryCredential )
          {
            dockerImage.push()
          }
        }
      }
    }
  }
}
