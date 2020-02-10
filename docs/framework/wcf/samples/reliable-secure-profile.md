---
title: Reliable Secure Profile
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: ef4680673f37655603a42f6da8aaf7eceaa01f56
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094941"
---
# <a name="reliable-secure-profile"></a>Reliable Secure Profile

Cet exemple montre comment composer WCF et [Reliable Secure Profile (RSP)](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html). Cet exemple illustre l’implémentation d’un canal [Make Connection](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf) , qui peut être composé avec une messagerie fiable et éventuellement un canal sécurisé pour créer une liaison sécurisée fiable basée sur la spécification RSP.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Discussions  
 Cet exemple illustre un scénario d'échange de messages bidirectionnel, asynchrone et fiable. Le service a un contrat duplex et le client implémente le contrat de rappel duplex. Le client initie une demande à un service, pour laquelle une réponse est attendue sur une connexion distincte. Le message de demande est envoyé de manière fiable. Le client ne souhaite pas ouvrir de point de terminaison d'écoute de son côté. Il interroge donc le service au moyen de demandes « Make Connection » de sorte que le service renvoie la réponse sur le canal arrière de cette demande « Make Connection ». Cet exemple montre comment bénéficier d'une communication en duplex fiable et sécurisée sur HTTP sans que le client n'expose de point de terminaison d'écoute (et ne crée d'exception de pare-feu).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Ouvrez la solution **ReliableSecureProfile** .  
  
2. Cliquez avec le bouton droit sur le projet de **service** dans **Explorateur de solutions**, sélectionnez **Déboguer**, **Démarrer une nouvelle instance** dans le menu contextuel. Cela démarre l'hôte de service.  
  
3. Cliquez avec le bouton droit sur le projet **client** dans **Explorateur de solutions**, sélectionnez **Déboguer**, **Démarrer une nouvelle instance** dans le menu contextuel. Cela démarre le client.  
  
4. Tapez une chaîne quelconque dans l'invite de la fenêtre de console du client et appuyez sur ENTRÉE. Cela envoie la chaîne entrée au service, qui calcule un hachage de cette chaîne.  
  
5. Examinez le résultat sur les fenêtres du client lorsque le service rappelle l'opération de contrat de rappel duplex pour afficher le résultat dans la fenêtre de console du client. Un délai intentionnel est appliqué au service pour simuler une longue opération de traitement des données.  
  
6. La surveillance du trafic HTTP (par l'un des outils d'analyse de réseau en ligne, comme le Moniteur réseau, Fiddler, etc.) montre qu'une séquence de communication est établie entre le client et le service comme stipulé par Reliable Secure Profile, et comment le client interroge le service avec des demandes « Make Connection ». Lorsque le service est prêt à renvoyer la réponse traitée, il utilise le canal arrière de la dernière demande « Make Connection » pour renvoyer les résultats.  
  
7. Appuyez sur ENTRÉE dans la fenêtre de console du service pour le fermer. Appuyez sur ENTRÉE dans la fenêtre de console du client pour le fermer.
