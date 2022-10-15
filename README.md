# Devops-Task
1. DB bağlantılı web server yaml file dosyaları hazırlandı.
2. Helm-Chart dosyaları hazırlandı.
3. Hazırladığım CloudFormation template us-east-1'da bir ec2 instance ayağa kaldırıyor (T3aMedium) (daha küçük boyutta bir instance K8S'i çalıştırmayablir.)    userdata:   docker, minikube, kubectl ve helm kuruyor.
4. Jenkins Sever'a:
    "cloudformation plugin" yüklemek gerekiyor ve
    "cloudformation full access" role atamak gerekiyor.
Jenkinsfile:
1. stage: uygulamanın deploy edileceği Infrastructure'ı CloudFormation ile ayağa kaldırıyor. 
2. stage: Ec2 instance ready olana kadar beklenmesini sağlıyor. 
3. stage: Uygulamayı Helm kullanarak instance'a deploy ediyor
