---
title: Utilisation des outils de développement WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183081"
---
# <a name="using-the-wcf-development-tools"></a>Utilisation des outils de développement WCF
Cette section décrit les outils de développement Visual Studio qui peuvent vous aider à développer votre service WCF.  
  
 Vous pouvez utiliser les modèles Visual Studio comme base pour construire rapidement votre propre service, puis utiliser WCF Service Auto Host et WCF Test Client pour déboiffer et tester votre service. Ces outils offrent un cycle de débogage et de test rapide et transparent tout en supprimant l'obligation de se limiter à un modèle d'hébergement à un stade précoce.  

 > [!NOTE]
 > À partir de Visual Studio 2017, les outils de développement WCF ne sont pas installés par défaut. Afin d’utiliser ces fonctionnalités, vous devez vous assurer que le composant De la Fondation De communication Windows est sélectionné dans l’installateur Visual Studio.
  
## <a name="the-wcf-developer-tools"></a>Outils WCF Developer  
 [Modèles Visual Studio WCF](wcf-vs-templates.md)  
  
 Vous pouvez utiliser le projet et les modèles d’objets Visual Studio prédéfinis dans Visual Studio pour construire rapidement les services WCF et les applications environnantes.  
  
 [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 Le WCF Service Auto Host (WcfSvcHost.exe) vous permet de lancer le Visual Studio debugger (F5) pour héberger et tester automatiquement un service que vous avez mis en œuvre. Vous pouvez ensuite tester le service à l’aide du client de test WCF (wcfTestClient.exe) ou de votre propre client pour trouver et corriger les erreurs potentielles.  
  
 [Client test WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 WCF Test Client (WcfTestClient.exe) est un outil d’interface utilisateur qui vous permet d’entrer les paramètres des types arbitraires, de soumettre cette entrée au service et de consulter la réponse que le service renvoie. Il offre une expérience de test de service transparente lorsqu’il est combiné avec WCF Service Auto Host.  
  
 [Génération de classes de type de données à partir de XML](generating-data-type-classes-from-xml.md)  
  
 Les données XML stockées dans le presse-papiers peuvent être collées dans une page de codes. Les classes définies dans les données sont converties en types de codes.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Utilisation des outils sans privilège d'administrateur  
 Pour permettre aux utilisateurs sans privilège d’administrateur de développer des services WCF,http://+:8731/Design_Time_Addressesun ACL (Access Control List) est créé pour le namespace " lors de l’installation de Visual Studio. La liste ACL a la valeur (UI), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur. Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste ACL ou ouvrir des ports supplémentaires. Cette liste ACL permet aux modèles WCF ou WF d'envoyer et de recevoir des données dans leur configuration par défaut. Il permet également aux utilisateurs d’utiliser le WCF Service Auto Host (wcfSvcHost.exe) sans leur accorder de privilèges d’administrateur.  
  
 Vous pouvez modifier l’accès à l’aide de l’outil Netsh.exe dans Windows Vista sous le compte administrateur élevé. L'utilisation de Netsh.exe est illustrée dans l'exemple suivant.  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Pour plus d’informations sur Netsh.exe, voir [Comment utiliser l’outil Netsh.exe et les commutateurs de ligne de commandement](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).  
  
## <a name="see-also"></a>Voir aussi

- [Modèles Visual Studio WCF](wcf-vs-templates.md)
- [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Client test WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
