---
title: Exécution des exemples Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: f4c7a7fa759d7339dee3d189540fb85f3883f828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594567"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Exécution des exemples Windows Communication Foundation
Les exemples Windows Communication Foundation (WCF) peuvent être exécutés dans une configuration à un seul ordinateur ou sur plusieurs ordinateurs. Tels qu'ils sont fournis, les exemples sont configurés pour être exécutés sur un ordinateur unique. Pour les exécuter sur plusieurs ordinateurs, il est nécessaire de modifier les paramètres de leur fichier de configuration. Les procédures suivantes permettent d'exécuter les exemples sur un même ordinateur ou sur plusieurs ordinateurs. Notez que ces procédures ne sont pas tout à fait les mêmes pour les exemples hébergés dans les services IIS et les exemples auto-hébergés. La plupart des exemples sont hébergés dans les services IIS. Consultez les informations contenues dans leur fichier lisezmoi respectif pour connaître leurs modalités d'hébergement.  
  
 Sur Windows Vista, les exemples qui ne sont pas hébergés dans IIS requièrent des privilèges élevés pour inscrire un écouteur auprès de http. sys. Utilisez Httpcfg.exe pour enregistrer les adresses d'écoute du service à l'aide du compte sous lequel le service s'exécute, ou lancez ce même service depuis une invite de commandes s'exécutant sous un compte d'administrateur.  
  
> [!NOTE]
> Avant de générer ou d’exécuter l’un des exemples WCF, assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1. Si le service est hébergé par IIS, assurez-vous que vous pouvez accéder au service à l’aide d’un navigateur en entrant l’adresse suivante : `http://localhost/servicemodelsamples/service.svc` . Une page de confirmation doit s'afficher en réponse. Si la page de confirmation ne s’affiche pas, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
2. Si le service est auto-hébergé, exécutez Service.exe à partir du répertoire \service\bin, situé dans le dossier correspondant à votre langue. L'activité du service s'affiche dans sa fenêtre de console.  
  
3. Exécutez client. exe à partir de \client\bin \\ , dans le dossier propre à la langue. L'activité du client s'affiche dans sa fenêtre de console.  
  
4. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Si le service est hébergé par IIS :  
  
    1. Créez un répertoire virtuel nommé ServiceModelSamples sur l'ordinateur de service. Le fichier de commandes Setupvroot. bat inclus dans [la procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md) peut être utilisé pour créer le répertoire de disque et le répertoire virtuel.  
  
    2. Copiez les fichiers du programme de service depuis %SystemDrive%\Inetpub\wwwroot\servicemodelsamples vers le répertoire virtuel ServiceModelSamples. Assurez-vous de copier les fichiers dans le répertoire \bin.  
  
    3. Assurez-vous que le service est accessible depuis l'ordinateur du client en utilisant un navigateur.  
  
     Si le service est auto-hébergé :  
  
    1. Sur l'ordinateur du service, créez un répertoire afin d'y stocker les fichiers lui correspondant.  
  
    2. Copiez les fichiers de programme du service figurant dans le dossier \service\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur de service.  
  
    3. Dans le fichier de configuration du service, modifiez l'adresse de la définition du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service. Remplacez toutes les occurrences de « localhost » de l'adresse par un nom de domaine complet.  
  
    4. Lancez Service.exe depuis une invite de commandes.  
  
2. Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.  
  
3. Définissez l'adresse de point de terminaison.  
  
    1. Si le service ne s'exécute pas sous un compte de domaine, ouvrez le fichier de configuration du client, puis modifiez l'adresse du point de terminaison en fonction de la nouvelle adresse de votre service. Remplacez toutes les occurrences de « localhost » de l'adresse par un nom de domaine complet.  
  
    2. Si le service s'exécute sous un compte de domaine, régénérez la configuration du client en exécutant Svcutil.exe par rapport au service. Pour plus d’informations sur l’exécution de Svcutil. exe, consultez [génération des exemples de Windows Communication Foundation](building-the-samples.md). Utilisez le fichier généré au lieu du fichier de configuration utilisé dans l'exemple. Le fichier de configuration généré contient des informations d'identité supplémentaires et contient tous les paramètres nécessaires à la connexion au point de terminaison du service bien qu'il s'agisse de paramètres par défaut. Pour plus d’informations sur les informations d’identité, consultez [identité du service et authentification](../feature-details/service-identity-and-authentication.md), et [\<identity>](../../configure-apps/file-schema/wcf/identity.md) .  
  
4. Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.  
  
### <a name="to-debug-a-service"></a>Pour déboguer un service  
  
1. Générez la solution (client et service) à l’aide du menu **générer** ou en appuyant sur Ctrl + Maj + B.  
  
2. Si le service est hébergé par IIS :  
  
    1. Activez le service à l’aide d’un navigateur en entrant l’adresse `http://localhost/servicemodelsamples/service.svc` .  
  
    2. Dans la solution, choisissez le menu **Déboguer** et l’élément **de menu attacher au processus** .  
  
    3. Cochez la case **Afficher les processus de tous les utilisateurs**.  
  
    4. Sélectionnez le processus de traitement W3wp.exe hôte afin de procéder au débogage (sélectionnez ASPNet_wp.exe sur Windows XP).  
  
3. Vous pouvez à présent définir des points d'arrêt dans le code de service et activer ces points pour les exceptions.  
  
4. Cliquez avec le bouton droit sur l’élément de projet client, puis choisissez **Déboguer**, **Démarrer une nouvelle instance**.  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Si le service est hébergé par IIS, pour des raisons de sécurité, supprimez la définition du répertoire virtuel ainsi que les autorisations accordées au cours des étapes d'installation (une fois l'exécution des exemples terminée).  
  
## <a name="see-also"></a>Voir aussi

- [Génération des exemples Windows Communication Foundation](building-the-samples.md)
- [Conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))
