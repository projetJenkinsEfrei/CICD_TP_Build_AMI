# CICD_TP_Build_AMI

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
- [Packer](#ansible)

## Prérequis

[(Back to top)](#sommaire)
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

[(Back to top)](#sommaire)

Le répertoire Ansible contient le playbook play.yml. Le playbook va permettre de déployer un serveur Web et une page web.

## Packer

[(Back to top)](#sommaire)

Le répertoire Packer contient le fichier buildAMI.json. Ce fichier permet de générer une AMI. Packer va utiliser le playbook play.yml car Ansible est notre provisionner.
Notre builder est 'amazon-ebs' pour interagir avec notre Cloud provider AWS.
