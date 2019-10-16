---
title: Utilisation des outils de développement WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 27cefb1ca1f4748f0d074ffdcd47cd6faa29da00
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320269"
---
# <a name="using-the-wcf-development-tools"></a>Utilisation des outils de développement WCF
Cette section décrit les outils de développement Visual Studio qui peuvent vous aider à développer vos WCFservice.  
  
 Vous pouvez utiliser les modèles Visual Studio comme base pour créer rapidement votre propre service, puis utiliser l’hôte auto du service WCF et le client test WCF pour déboguer et tester votre service. Ces outils offrent un cycle de débogage et de test rapide et transparent tout en supprimant l'obligation de se limiter à un modèle d'hébergement à un stade précoce.  
 
 > [!NOTE]
 > À compter de Visual Studio 2017, les outils de développement WCF ne sont pas installés par défaut. Pour pouvoir utiliser ces fonctionnalités, vous devez vous assurer que le composant Windows Communication Foundation est sélectionné dans le programme d’installation de Visual Studio.
  
## <a name="the-wcf-developer-tools"></a>Outils WCF Developer  
 [Modèles Visual Studio WCF](wcf-vs-templates.md)  
  
 Vous pouvez utiliser les modèles de projet et d’élément Visual Studio prédéfinis dans Visual Studio pour générer rapidement des services WCF et des applications environnantes.  
  
 [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 L’hôte auto du service WCF (WcfSvcHost. exe) vous permet de lancer le débogueur Visual Studio (F5) pour héberger et tester automatiquement un service que vous avez implémenté. Vous pouvez ensuite tester le service à l’aide du client test WCF (wcfTestClient. exe) ou de votre propre client pour rechercher et corriger les erreurs potentielles.  
  
 [Client test WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 Le client test WCF (WcfTestClient. exe) est un outil d’interface graphique utilisateur qui vous permet d’entrer des paramètres de types arbitraires, d’envoyer cette entrée au service et d’afficher la réponse renvoyée par le service. Il fournit une expérience de test de service transparente lorsqu’il est associé à l’hôte auto du service WCF.  
  
 [Génération de classes de type de données à partir de XML](generating-data-type-classes-from-xml.md)  
  
 Les données XML stockées dans le presse-papiers peuvent être collées dans une page de codes. Les classes définies dans les données sont converties en types de codes.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Utilisation des outils sans privilège d'administrateur  
 Pour permettre aux utilisateurs sans privilège d’administrateur de développer des services WCF, une liste de contrôle d’accès (liste de Access Control) est créée pour l’espace de noms « http://+:8731/Design_Time_Addresses  » pendant l’installation de Visual Studio. La liste ACL a la valeur (UI), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur. Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste ACL ou ouvrir des ports supplémentaires. Cette liste ACL permet aux modèles WCF ou WF d'envoyer et de recevoir des données dans leur configuration par défaut. Il permet également aux utilisateurs d’utiliser l’hôte auto du service WCF (wcfSvcHost. exe) sans leur accorder de privilèges d’administrateur.  
  
 Vous pouvez modifier l'accès à l'aide de l'outil Netsh.exe dans [!INCLUDE[wv](../../../includes/wv-md.md)] par le biais du compte d'administrateur supérieur. L'utilisation de Netsh.exe est illustrée dans l'exemple suivant.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Pour plus d’informations sur netsh. exe, consultez [comment utiliser l’outil netsh. exe et les commutateurs de ligne de commande](https://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Voir aussi

- [Modèles Visual Studio WCF](wcf-vs-templates.md)
- [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Client test WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
