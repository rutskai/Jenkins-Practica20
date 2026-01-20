pipeline {
    agent any
    
    environment {
        APP = "MiAplicacion"
        ENTORNO = "DEV"
        MENSAJE = "Pipeline de prueba para despliegue"
    }

    stages {
        stage('Info') {
            steps {
                echo "===== Información del entorno ====="
                echo "APP: ${env.APP}"
                echo "ENTORNO: ${env.ENTORNO}"
                echo "MENSAJE: ${env.MENSAJE}"
                echo "JOB_NAME: ${env.JOB_NAME}"
                echo "BUILD_NUMBER: ${env.BUILD_NUMBER}"
            }
        }

        stage('Aprobación') {
            steps {
                input message: "¿Deseas continuar con el despliegue?", ok: "Continuar"
            }
        }

        stage('Simular despliegue') {
            steps {
                echo "Desplegando ${env.APP} en ${env.ENTORNO}..."
            }
        }
    }

    post {
        always {
            echo "Pipeline finalizado"
        }
        success {
            echo "El despliegue fue exitoso!"
        }
        failure {
            echo "El pipeline ha fallado"
        }
        aborted {
            echo "El pipeline fue cancelado manualmente"
        }
    }
}
