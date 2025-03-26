pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Obtiene el código fuente del repositorio
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // Comandos para construir el proyecto
                sh 'mvn clean install' // Ejemplo para proyectos Maven
            }
        }
        stage('Test') {
            steps {
                // Comandos para ejecutar pruebas unitarias
                sh 'mvn test' // Ejemplo para proyectos Maven
            }
        }
        stage('Deploy to Asignatura Container') {
            when {
                branch 'main'
            }
            steps {
                // Comandos para desplegar en el contenedor de la asignatura
                sh 'docker-compose -f docker-compose-asignatura.yml up -d'
            }
        }
        stage('Deploy to Docker Container within Asignatura') {
            when {
                branch 'main'
            }
            steps {
                // Comandos para desplegar en un contenedor Docker dentro del contenedor de la asignatura
                sh 'docker build -t proyecto .'
                sh 'docker run -d --name proyecto_container proyecto'
            }
        }
    }
    // Definir las ramas en las que se ejecutarán ciertas etapas
    post {
        always {
            // Acciones que se ejecutan siempre, independientemente de la rama
        }
        success {
            // Acciones que se ejecutan solo si el pipeline es exitoso
        }
        failure {
            // Acciones que se ejecutan solo si el pipeline falla
        }
    }
}
