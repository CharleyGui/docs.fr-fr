---
title: Local Channel
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 11f3e4fe07ffa285f72ba8fd92224a3ba78d238b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656038"
---
# <a name="local-channel"></a>Local Channel
Local Channel est un canal de transport de Windows Communication Foundation (WCF) qui est utilisé pour la communication au sein du même domaine d’application. Cela peut être utile pour les scénarios où le client et le service s’exécutent dans le même domaine d’application et où la charge liée à la pile de canaux WCF classique (sérialisation et désérialisation de messages) doit être évitée.  
  
## <a name="demonstrates"></a>Démonstrations  
 Local Channel  
  
## <a name="discussion"></a>Discussion  
 Cet exemple est composé de deux fichiers projet :  
  
- **LocalChannel**: La représentation par programme du canal local dans le domaine d’application actuel. Dans ce projet, le composant expéditeur place le message dans une file d'attente en mémoire et le composant récepteur retire le message de la file d'attente pour le recevoir.  
  
- **ClientAndService**: Ce projet héberge un service dans une application console, puis exécute un client pour appeler le service à partir du même domaine d’application.  
  
 Le canal local est conçu pour ignorer la pile de canaux et le processus de sérialisation afin de gagner en vitesse. Le canal de transport local est implémenté à l'aide d'une file d'attente pour transporter les appels de service du client au service et pour retourner la valeur au client. Au lieu de sérialiser des paramètres et des valeurs de retour, l'exemple copie les objets.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Générez et exécutez la solution LocalChannel.  
  
2. L'hôte du service démarre et le client appelle le service en utilisant le canal local. Une fenêtre de console apparaît pour afficher le résultat de l'appel de service.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
