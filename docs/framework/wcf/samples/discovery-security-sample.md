---
title: Exemple Discovery Security
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: f644d0098ddb09ee115c6d6429ce7b005ee0b77a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650112"
---
# <a name="discovery-security-sample"></a>Exemple Discovery Security
La spécification Discovery n'exige pas que les points de terminaison participant au processus de découverte soient sécurisés. L'ajout de la sécurité aux messages de découverte atténue divers types d'attaques (altération de messages, déni de service, relecture, usurpation). Cet exemple implémente des canaux personnalisés qui calculent et vérifient des signatures de message utilisant le format de signature compact (décrit dans la section 8.2 de la spécification WS-Discovery). L’exemple prend en charge la [spécification Discovery 2005](https://go.microsoft.com/fwlink/?LinkId=177912) et [version 1.1](https://go.microsoft.com/fwlink/?LinkId=179677).  
  
 Le canal personnalisé est appliqué en plus de la pile de canaux existante pour les points de terminaison de découverte et d'annonce. De cette façon, un en-tête de signature est appliqué pour chaque message envoyé. La signature est vérifiée sur les messages reçus, qui sont supprimés s’ils ne comportent pas de signature ou si celle-ci ne correspond pas. Pour signer et vérifier des messages, l'exemple utilise des certificats.  
  
## <a name="discussion"></a>Discussion  
 WCF est très extensible et offre aux utilisateurs la possibilité de personnaliser des canaux à leur gré. L’exemple implémente un élément de liaison sécurisée de découverte qui génère des canaux sécurisés. Les canaux sécurisés appliquent et vérifient les signatures des messages et sont appliqués en plus de la pile actuelle.  
  
 L’élément de liaison sécurisée génère des écouteurs et fabriques de canaux sécurisés.  
  
## <a name="secure-channel-factory"></a>Fabrique de canaux sécurisés  
 La fabrique de canaux sécurisés crée des canaux de sortie ou duplex qui ajoutent une signature compacte aux en-têtes de message. Pour garder les messages aussi petits que possible, le format de signature compact est utilisé. La structure d'une signature compacte est représentée dans l'exemple suivant.  
  
```xml  
<d:Security ... >   
  [<d:Sig Scheme="xs:anyURI"   
         [KeyId="xs:base64Binary"]?  
          Refs="..."  
         [PrefixList]="xs:NMTOKENS"   
          Sig="xs:base64Binary"   
          ... />]?  
  ...   
</d:Security>  
```  
  
> [!NOTE]
>  Le `PrefixList` a été ajouté dans le protocole Discovery version 2008.  
  
 Pour calculer la signature, l’exemple identifie les éléments de signature développés. Une signature XML (`SignedInfo`) est créée, à l'aide du préfixe d'espace de noms `ds`, comme requis par la spécification WS-Discovery. Le corps et tous les en-têtes des espaces de noms de découverte et d'adressage sont référencés dans la signature et ne peuvent donc pas être falsifiés. Chaque élément référencé est transformé à l’aide de la canonicalisation Exclusive (http://www.w3.org/2001/10/xml-exc-c14n# ), et ensuite une valeur de condensat SHA-1 est calculée (http://www.w3.org/2000/09/xmldsig#sha1 ). En fonction de tous les éléments référencés et leurs valeurs digest, la valeur de signature est calculée à l’aide de l’algorithme RSA (http://www.w3.org/2000/09/xmldsig#rsa-sha1 ).  
  
 Les messages sont signés avec un certificat spécifié par le client. L’emplacement et le nom du magasin, ainsi que le nom de sujet du certificat doivent être spécifiés au moment de la création de l’élément de liaison. Le `KeyId` de la signature compacte représente l'identificateur de clé du jeton de signature et constitue l'identificateur de la clé du sujet (SKI, Subject Key Identifier) du jeton de signature ou, si le SKI n'existe pas, un hachage SHA-1 de la clé publique du jeton de signature.  
  
## <a name="secure-channel-listener"></a>Écouteur de canal sécurisé  
 L'écouteur de canal sécurisé crée des canaux d'entrée ou duplex qui vérifient la signature compacte dans les messages reçus. Pour vérifier la signature, le `KeyId` spécifié dans la signature compacte jointe au message est utilisé afin de sélectionner un certificat dans le magasin spécifié. Si le message n'a pas de signature ou si la vérification de la signature échoue, les messages sont supprimés. Pour utiliser la liaison sécurisée, l’exemple définit une fabrique qui crée les <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> et <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> personnalisés avec l’élément de liaison sécurisée de découverte ajouté. Ces points de terminaison sécurisés peuvent être utilisés dans des écouteurs d'annonces de découverte et des services détectables.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'exemple comporte une bibliothèque et 4 applications console :  
  
- **DiscoverySecurityChannels**: Une bibliothèque qui expose la liaison sécurisée. Cette bibliothèque calcule et vérifie la signature compacte des messages sortants/entrants.  
  
- **Service** : Service exposant le contrat ICalculatorService, auto-hébergé. Ce service est marqué comme étant détectable. L'utilisateur spécifie les informations du certificat utilisé pour signer des messages en spécifiant l'emplacement et le nom du magasin, ainsi que le nom du sujet ou autre identificateur unique pour le certificat, et le magasin où se trouvent les certificats clients (certificats utilisés pour vérifier la signature des messages entrants). Sur la base de ces informations, un UdpDiscoveryEndpoint avec sécurité accrue est généré et utilisé.  
  
- **Client**: Cette classe tente de découvrir un ICalculatorService et appeler des méthodes sur le service. Là encore, un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> avec sécurité accrue est généré et utilisé pour signer et vérifier les messages.  
  
- **AnnouncementListener**: Un service auto-hébergé qui écoute les annonces en ligne et hors connexion et utilise le point de terminaison d’annonce sécurisé.  
  
> [!NOTE]
>  Si Setup.bat est exécuté plusieurs fois, des certificats sont dupliqués et le gestionnaire de certificats vous invite à choisir le certificat à ajouter. Dans ce cas, Setup.bat doit être abandonné et Cleanup.bat doit être appelé, car les doublons ont déjà été créés. Cleanup.bat vous invite également à choisir le certificat à supprimer. Sélectionnez un certificat dans la liste et continuez à exécuter Cleanup.bat jusqu'à ce qu'il ne reste aucun certificat.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1. Exécutez le script Setup.bat à partir d’une invite de commandes développeur pour Visual Studio. L'exemple utilise des certificats pour signer et vérifier des messages. Le script crée les certificats à l'aide de Makecert.exe, puis les installe à l'aide de Certmgr.exe. Le script doit être exécuté avec des privilèges d'administrateur.  
  
2. Pour générer et exécuter l’exemple, ouvrez le fichier Security.sln dans Visual Studio et choisissez **Rebuild All**. Mettre à jour les propriétés de solution pour démarrer plusieurs projets : sélectionnez **Démarrer** pour tous les projets à l’exception de DiscoverySecureChannels. Exécutez la solution normalement.  
  
3. Lorsque vous en avez terminé avec l'exemple, exécutez le script Cleanup.bat, qui supprime les certificats créés pour cet exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
