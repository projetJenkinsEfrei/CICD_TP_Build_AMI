# CICD_TP_Build_AMI


<div align="center">
  <img src="https://blog.sitm.ac.in/wp-content/uploads/2019/09/devops-660x330.png" width="210" height="110"/>
  <br>
  <br>
</div>


[![forthebadge](https://forthebadge.com/images/badges/uses-git.svg)](https://forthebadge.com)

<table>
<tr>
<td>
Dans le cadre d'un projet qui suit l'approche DevOps on réalise le déploiement d'une application.
Pour cela on utilise la plateforme d'intégration continu Jenkins.  

Ici ce dépot contient deux répertoires : Ansible et Packer. 
</td>
</tr>
</table>


## Sommaire

- [Prérequis](#prérequis)
- [Ansible](#ansible)
- [Packer](#packer)
- Lien

## Prérequis

- Jenkins

On utilise Jenkins dans la version 1.5.1

```sh
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add - 
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list' 
sudo apt update 
sudo apt install default-jre jenkins --yes 
sudo systemctl enable jenkins 
sudo systemctl start jenkins 
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

- Compte AWS (+création d'un rôle)

On utilise le fournisseur de Cloud AWS. On créer un rôle pour que le fichier Packer puisse interagir avec l’API AWS. 

## Ansible

Le répertoire Ansible contient le playbook play.yml. Le playbook va permettre de déployer un serveur Web et une page web.

## Packer

Le répertoire Packer contient le fichier buildAMI.json. Ce fichier permet de générer une AMI. Packer va utiliser le playbook play.yml car Ansible est notre provisionner.
Notre builder est 'amazon-ebs' pour interagir avec notre Cloud provider AWS.

## Lien 

[(Back to top)](#sommaire)

Voici ci-dessous quelques liens de dépot à consulter pour avoir plus d'information sur le déploiement.

- Liens :
  - https://github.com/birintha/CICD_TP_Deploy_Infra 
  - https://github.com/birintha/CICD_TP_Deploy_WebApp
