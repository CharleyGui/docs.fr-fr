---
title: Exemple SystemWebRouting Integration
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143952"
---
# <a name="systemwebrouting-integration-sample"></a>Exemple SystemWebRouting Integration
Cet exemple illustre l'intégration de la couche d'hébergement avec les classes de l'espace de noms <xref:System.Web.Routing>. Les classes de l'espace de noms <xref:System.Web.Routing> permettent à une application d'utiliser des URL qui ne correspondent pas directement à une ressource physique. L’utilisation du routage Web permet au développeur de créer des adresses virtuelles pour HTTP qui sont ensuite cartographiées vers les services WCF réels. Cela peut être utile lorsqu'un service WCF doit être hébergé sans requérir de fichier ou ressource physique, ou lorsque des services doivent être accessibles via des URL qui ne contiennent pas de fichiers tels que .html ou .aspx. Cet exemple montre comment utiliser la classe <xref:System.Web.Routing.RouteTable> pour créer des URI virtuels qui mappent aux services en cours d'exécution définis dans global.asax.

> [!NOTE]
> Les classes de l'espace de noms <xref:System.Web.Routing> ne fonctionnent que pour des services hébergés sur HTTP.  
  
Cet exemple utilise WCF pour créer deux `movies` flux RSS : un flux et un `channels` flux. Les URL pour activer les services ne contiennent pas `Application_Start` d’extension et sont enregistrées dans la méthode de la `Global` classe dérivée de la <xref:System.Web.HttpApplication> classe.  
  
> [!NOTE]
> Cet échantillon ne fonctionne que dans les services d’information Internet (IIS) 7.0 et plus tard, car IIS 6.0 utilise une méthode différente pour soutenir les URL sans extension.  

#### <a name="to-download-this-sample"></a>Pour télécharger cet exemple
  
Cet échantillon peut déjà être installé sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  

`<InstallDrive>:\WF_WCF_Samples`  

 Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1. À l’aide de Visual Studio, ouvrez le fichier WebRoutingIntegration.sln.  
  
2. Pour exécuter la solution et démarrer le serveur de développement Web, appuyez sur F5.  
  
     Une liste des répertoires de l'exemple s'affiche. Notez l'absence de fichiers ayant l'extension .svc.  
  
3. Dans la barre `movies` d’adresse, ajoutez à `http://localhost:[port]/movies` l’URL, de sorte qu’elle se lit et appuyez sur ENTER.  
  
     Le flux movies s'affiche dans le navigateur.  
  
4. Dans la barre `channels` d’adresse, ajouter à `http://localhost:[port]/channels` l’URL, de sorte que se lit et appuyez sur ENTER.  
  
     Le flux channels s'affiche dans le navigateur.  
  
5. Fermez le navigateur Web en appuyant sur ALT+F4.  
  
     Si le serveur de développement n’est pas sorti, cliquez à droite sur l’icône de la zone de notification et **sélectionnez Stop**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Pour utiliser cet exemple avec hébergement dans IIS  
  
1. À l’aide de Visual Studio, ouvrez le fichier WebRoutingIntegration.sln.  
  
2. Générez le projet en appuyant sur Ctrl+Maj+B.  
  
3. Créez une application Web dans le Gestionnaire des services Internet (IIS).  
  
    1. Dans IIS Manager, cliquez à droite sur le **site Web par défaut** et sélectionnez Ajouter une **application**.  
  
    2. Pour le **pseudonyme**, tapez dans `WebRoutingIntegration`.  
  
    3. Pour le **chemin physique**, sélectionnez le dossier Service à l’intérieur du projet.  
  
    4. Appuyez sur **OK**.  
  
4. Démarrez l’application, en cliquant à droite sur l’application Web et en sélectionnant **Manage Application,** puis **parcourez.**  
  
5. Dans la barre `movies` d’adresse, ajouter à `http://localhost:[port]/movies` l’URL, de sorte que se lit et appuyez sur ENTER.  
  
     Le flux movies s'affiche dans le navigateur.  
  
6. Dans la barre `channels` d’adresse, ajouter à `http://localhost:[port]/channels` l’URL, de sorte que se lit et appuyez sur ENTER.  
  
     Le flux channels s'affiche dans le navigateur.  
  
7. Fermez le navigateur Web en appuyant sur ALT+F4.  
  
 Cet exemple montre que la couche d'hébergement est capable de composer avec les classes de l'espace de noms <xref:System.Web.Routing> pour router les requêtes de services hébergés sur HTTP.  
  
> [!NOTE]
> Vous devez mettre à jour la version de pool d’applications par défaut à .NET Framework 4 si elle est configurée à la version 2.  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
