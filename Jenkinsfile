pipeline {
    agent any

    stages {
        stage('Obtener versiones') {
            steps {
                script {
                    def timestamp = new Date().format("yyyyMMddHHmmss")
                    def versionFile = "info_versiones_${timestamp}.txt"
                    sh "java -version 2>&1 | tee ${versionFile}"
                    sh "jenkins --version >> ${versionFile}"
                    archiveArtifacts artifacts: versionFile, fingerprint: true
                }
            }
        }

        stage('Escanear puertos abiertos') {
            steps {
                script {
                    def timestamp = new Date().format("yyyyMMddHHmmss")
                    def scanFile = "escaneo_puertos_${timestamp}.txt"
                    def ip = sh(script: """hostname -I | awk '{print $1}'""", returnStdout: true).trim()
                    sh "nmap -p- ${ip} > ${scanFile}"
                    archiveArtifacts artifacts: scanFile, fingerprint: true
                }
            }
        }

        stage('Generar hashes SHA-256') {
            steps {
                script {
                    def timestamp = new Date().format("yyyyMMddHHmmss")
                    def hashFile = "verificacion_integridad_${timestamp}.txt"
                    def targetPath = "/var/lib/jenkins/workspace/Proyecto_Seguridad/ficheros_importantes"
                    sh "find ${targetPath} -type f -exec sha256sum {} + > ${hashFile}"
                    archiveArtifacts artifacts: hashFile, fingerprint: true
                }
            }
        }
    }
}
