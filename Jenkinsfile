pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    // environment{
    //    ArtifactId = readMavenPom().getArtifactId()
    //    Version = readMavenPom().getVersion()
    //    Name = readMavenPom().getName()
    //    GroupId = readMavenPom().getGroupId()
    // }
    stages {
        // Specify various stage with in stages
        
        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'
            }
        }

        // Stage 3 : Deploying
        // stage ('Deploy'){
        //     steps {
        //         echo ' deploying......'

        //     }
        // }
        stage ('Sonarqube Analysis'){
            steps {
                echo ' Source code published to Sonarqube for SCA....'
                withSonarQubeEnv('sonarqube'){
                    sh 'mvn sonar:sonar'
                }

            }
        }


        //stage 3 : Publish the artifacts to Nexus
        // stage ('Publish to Nexus') {
        //     steps {
        //         script {

        //             def NexusRepo = Version.endsWith("SNAPSHOT") ? "VinaysDevOpsLab-SNAPSHOT" : "VinaysDevOpsLab-RELEASE"

        //             nexusArtifactUploader artifacts: 
        //             [[artifactId: "${ArtifactId}",  
        //             classifier: '', 
        //             file: "target/${ArtifactId}-${Version}.war", 
        //             type: 'war']], 
        //             credentialsId: 'db40c03e-d6f2-4c60-8558-1cfa5bb1d2b6', 
        //             groupId: "${GroupId}", 
        //             nexusUrl: '172.20.10.68:8081', 
        //             nexusVersion: 'nexus3', 
        //             protocol: 'http', 
        //             repository: "${NexusRepo}", 
        //             version: "${Version}"
        //         }
        //     }
        // }

        // Stage 4 : Print some information
        // stage ('Print Environment variables'){
        //     steps {
        //         echo "Artifact ID is '${ArtifactId}'"
        //         echo "Version is '${Version}'"
        //         echo "GroupID is '${GroupId}'"
        //         echo "Name is '${Name}'"
        //     }
        // }

        // Stage 5 : Deploying the build artifact to Tomcat
        // stage ('Deploy to Tomcat'){
        //     steps {
        //         echo "Deploying tomcat ...."
        //         sshPublisher(publishers: 
        //         [sshPublisherDesc(
        //             configName: 'Ansible_Controller', 
        //             transfers: [
        //                 sshTransfer(
        //                     cleanRemote: false, 
        //                     excludes: '', 
        //                     execCommand: 'ansible-playbook /opt/playbooks/downloadanddeploy_as_tomcat_user.yaml -i /opt/playbooks/hosts', 
        //                     execTimeout: 120000, 
        //                     flatten: false, 
        //                     makeEmptyDirs: false, 
        //                     noDefaultExcludes: false, 
        //                     patternSeparator: '[, ]+', 
        //                     remoteDirectory: '', 
        //                     remoteDirectorySDF: false, 
        //                     removePrefix: '', 
        //                     sourceFiles: '')
        //             ], 
        //             usePromotionTimestamp: false, 
        //             useWorkspaceInPromotion: false, 
        //             verbose: false)])
            
        //     }
        // }

// Stage 6 : Deploying the build artifact to Docker
        // stage ('Deploy to Docker'){
        //     steps {
        //         echo "Deploying docker ...."
        //         sshPublisher(publishers: 
        //         [sshPublisherDesc(
        //             configName: 'Ansible_Controller', 
        //             transfers: [
        //                 sshTransfer(
        //                     cleanRemote: false, 
        //                     excludes: '', 
        //                     execCommand: 'ansible-playbook /opt/playbooks/downloadanddeploy_docker.yaml -i /opt/playbooks/hosts', 
        //                     execTimeout: 120000, 
        //                     flatten: false, 
        //                     makeEmptyDirs: false, 
        //                     noDefaultExcludes: false, 
        //                     patternSeparator: '[, ]+', 
        //                     remoteDirectory: '', 
        //                     remoteDirectorySDF: false, 
        //                     removePrefix: '', 
        //                     sourceFiles: '')
        //             ], 
        //             usePromotionTimestamp: false, 
        //             useWorkspaceInPromotion: false, 
        //             verbose: false)])
            
        //     }
        // }




    }

}