pipeline {
    agent any

    environment {
        // Define aquí las variables de entorno necesarias
        // EJEMPLO: PATH_TO_PROJECT = '/ruta/a/tu/proyecto'
    }

    stages {
        stage('Build') {
            steps {
                // Paso para la construcción del proyecto
                echo 'Construyendo el proyecto...'
                // Añade aquí los comandos necesarios para construir tu proyecto
                // EJEMPLO: sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                // Paso para ejecutar las pruebas
                echo 'Ejecutando pruebas...'
                // Añade aquí los comandos necesarios para ejecutar tus pruebas
                // EJEMPLO: sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                // Paso para desplegar el proyecto
                echo 'Desplegando el proyecto...'
                // Añade aquí los comandos necesarios para desplegar tu proyecto
                // EJEMPLO: sh 'docker-compose up -d'
            }
        }
    }

    post {
        always {
            // Acciones que se ejecutan siempre al finalizar el pipeline
            echo 'Pipeline finalizado.'
        }
        success {
            // Acciones que se ejecutan si el pipeline finaliza con éxito
            echo 'Pipeline completado con éxito.'
        }
        failure {
            // Acciones que se ejecutan si el pipeline falla
            echo 'Pipeline fallido.'
        }
    }
}
