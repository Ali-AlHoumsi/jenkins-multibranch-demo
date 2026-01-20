pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // هنا نقوم بتنفيذ السكريبت وحفظ الناتج في ملف نصي
                sh 'chmod +x app.sh'
                sh './app.sh > build-output.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                // محاكاة اختبار بسيط
                sh 'grep "1.0" build-output.txt'
            }
        }
    }

    post {
        success {
            // هذه الخطوة هي المسؤولة عن حفظ الـ Artifact
            // سنحفظ الملف الناتج ليمكن تحميله لاحقاً
            archiveArtifacts artifacts: 'build-output.txt', fingerprint: true
            echo 'Archiving completed successfully!'
        }
    }
