---
title: Client Validation
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: a8cbb077488c222798bfd4b7f88f2de63f5e422d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651023"
---
# <a name="client-validation"></a>Client Validation
Les services publient fréquemment des métadonnées pour activer la génération et la configuration automatiques de types de proxy clients. Lorsque le service n'est pas approuvé, les applications clientes doivent valider que les métadonnées se conforment à la stratégie de l'application cliente en ce qui concerne la sécurité, les transactions, le type de contrat de service, etc. L'exemple suivant montre comment écrire un comportement de point de terminaison client qui valide le point de terminaison de service pour garantir que ce dernier est fiable.  
  
 Le service expose quatre points de terminaison de service. Le premier point de terminaison utilise WSDualHttpBinding, le deuxième utilise l’authentification NTLM, le troisième active le flux de transaction et le quatrième utilise l’authentification basée sur les certificats.  
  
 Le client utilise la classe <xref:System.ServiceModel.Description.MetadataResolver> pour récupérer les métadonnées pour le service. Le client met en vigueur une stratégie d’interdiction des liaisons duplex, d’authentification NTLM et de flux de transaction à l’aide d’un comportement de validation. Pour chaque <xref:System.ServiceModel.Description.ServiceEndpoint> instance importé à partir des métadonnées du service, l’application cliente ajoute une instance de la `InternetClientValidatorBehavior` comportement de point de terminaison pour le <xref:System.ServiceModel.Description.ServiceEndpoint> avant d’utiliser un client Windows Communication Foundation (WCF) pour se connecter à le point de terminaison. La méthode `Validate` du comportement s'exécute avant qu'une opération sur le service soit appelée et met en vigueur la stratégie du client en levant `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Pour générer l'exemple  
  
1. Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1. Ouvrez une invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez Setup.bat à partir du dossier d’installation de l’exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.  
  
2. Exécutez l'application de service à partir de \service\bin\Debug.  
  
3. Exécutez l'application cliente à partir de \client\bin\Debug. L'activité du client s'affiche sur son application de console.  
  
4. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour obtenir des exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Supprimez les certificats en exécutant Cleanup.bat une fois l'exemple terminé. D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Sur le serveur, dans une invite de commandes développeur pour Visual Studio s’exécuter avec des privilèges d’administrateur, tapez `setup.bat service`. En cours d’exécution `setup.bat` avec la `service` argument crée un certificat de service portant le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé Service.cer.  
  
2. Sur le serveur, modifiez le fichier App.config en fonction du nouveau nom du certificat. Autrement dit, modifiez le `findValue` d’attribut dans le [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) élément au nom de domaine complet de l’ordinateur.  
  
3. Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.  
  
4. Sur le client, ouvrez une invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et le type `setup.bat client`. En cours d’exécution `setup.bat` avec la `client` argument crée un certificat client appelé Client.com et exporte le certificat client vers un fichier nommé Client.cer.  
  
5. Dans le fichier client.cs, modifiez la valeur de l'adresse du point de terminaison MEX et `findValue` pour que le certificat de serveur par défaut corresponde à la nouvelle adresse de votre service. Pour ce faire, remplacez localhost par le nom de domaine complet du serveur. Régénérez.  
  
6. Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
7. Sur le client, exécutez ImportServiceCert.bat dans une invite de commandes développeur pour Visual Studio ouverte avec des privilèges d’administrateur. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
8. Sur le serveur, exécutez ImportClientCert.bat dans une invite de commandes développeur pour Visual Studio ouverte avec des privilèges d’administrateur. Le certificat client est ainsi importé à partir du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.  
  
9. Sur l'ordinateur de service, générez le projet de service dans Visual Studio et exécutez service.exe.  
  
10. Sur l'ordinateur client, exécutez client.exe.  
  
    1. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour obtenir des exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
    > [!NOTE]
    >  Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs. Si vous avez exécuté les exemples WCF qui utilisent des certificats sur plusieurs ordinateurs, assurez-vous d’effacer les certificats de service qui ont été installés dans le CurrentUser - TrustedPeople stocker. Pour ce faire, utilisez la ligne de commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)
