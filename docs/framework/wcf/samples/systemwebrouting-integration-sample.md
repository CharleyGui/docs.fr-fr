---
title: Exemple SystemWebRouting Integration
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: a91763e7dacb04a68cfea1079d55bbc1eda01668
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094889"
---
# <a name="systemwebrouting-integration-sample"></a>Exemple SystemWebRouting Integration
Cet exemple illustre l'intégration de la couche d'hébergement avec les classes de l'espace de noms <xref:System.Web.Routing>. Les classes de l'espace de noms <xref:System.Web.Routing> permettent à une application d'utiliser des URL qui ne correspondent pas directement à une ressource physique. L’utilisation du routage Web permet au développeur de créer des adresses virtuelles pour HTTP qui sont ensuite remappées aux services WCF réels. Cela peut être utile lorsqu'un service WCF doit être hébergé sans requérir de fichier ou ressource physique, ou lorsque des services doivent être accessibles via des URL qui ne contiennent pas de fichiers tels que .html ou .aspx. Cet exemple montre comment utiliser la classe <xref:System.Web.Routing.RouteTable> pour créer des URI virtuels qui mappent aux services en cours d'exécution définis dans global.asax. 

> [!NOTE]
> Les classes de l'espace de noms <xref:System.Web.Routing> ne fonctionnent que pour des services hébergés sur HTTP.  
  
Cet exemple utilise WCF pour créer deux flux RSS : un flux `movies` et un flux `channels`. Les URL permettant d’activer les services ne contiennent pas d’extension et sont inscrites dans la méthode `Application_Start` de la classe `Global` dérivée de la classe <xref:System.Web.HttpApplication>.  
  
> [!NOTE]
> Cet exemple fonctionne uniquement dans Internet Information Services (IIS) 7,0 et versions ultérieures, car IIS 6,0 utilise une méthode différente pour prendre en charge les URL sans extension.  

#### <a name="to-download-this-sample"></a>Pour télécharger cet exemple
  
Cet exemple est peut-être déjà installé sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1. À l’aide de Visual Studio, ouvrez le fichier WebRoutingIntegration. sln.  
  
2. Pour exécuter la solution et démarrer le serveur de développement Web, appuyez sur F5.  
  
     Une liste des répertoires de l'exemple s'affiche. Notez l'absence de fichiers ayant l'extension .svc.  
  
3. Dans la barre d’adresses, ajoutez `movies` à l’URL, afin qu’elle lise `http://localhost:[port]/movies` et appuyez sur entrée.  
  
     Le flux movies s'affiche dans le navigateur.  
  
4. Dans la barre d’adresses, ajoutez `channels` à l’URL, afin que soit lit `http://localhost:[port]/channels` et appuyez sur entrée.  
  
     Le flux channels s'affiche dans le navigateur.  
  
5. Fermez le navigateur Web en appuyant sur ALT+F4.  
  
     Si le serveur de développement ne s’est pas arrêté, cliquez avec le bouton droit sur l’icône de la zone de notification et sélectionnez **arrêter**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Pour utiliser cet exemple avec hébergement dans IIS  
  
1. À l’aide de Visual Studio, ouvrez le fichier WebRoutingIntegration. sln.  
  
2. Générez le projet en appuyant sur Ctrl+Maj+B.  
  
3. Créez une application Web dans le Gestionnaire des services Internet (IIS).  
  
    1. Dans le gestionnaire des services Internet, cliquez avec le bouton droit sur le **site Web par défaut** et sélectionnez **Ajouter une application**.  
  
    2. Pour l' **alias**, tapez `WebRoutingIntegration`.  
  
    3. Pour le **chemin d’accès physique**, sélectionnez le dossier de service à l’intérieur du projet.  
  
    4. Appuyez sur **OK**.  
  
4. Démarrez l’application, en cliquant avec le bouton droit sur l’application Web et en sélectionnant **gérer l’application** , puis **Parcourir**.  
  
5. Dans la barre d’adresses, ajoutez `movies` à l’URL, afin que soit lit `http://localhost:[port]/movies` et appuyez sur entrée.  
  
     Le flux movies s'affiche dans le navigateur.  
  
6. Dans la barre d’adresses, ajoutez `channels` à l’URL, afin que soit lit `http://localhost:[port]/channels` et appuyez sur entrée.  
  
     Le flux channels s'affiche dans le navigateur.  
  
7. Fermez le navigateur Web en appuyant sur ALT+F4.  
  
 Cet exemple montre que la couche d'hébergement est capable de composer avec les classes de l'espace de noms <xref:System.Web.Routing> pour router les requêtes de services hébergés sur HTTP.  
  
> [!NOTE]
> Vous devez mettre à jour la version du pool d’applications par défaut sur .NET Framework 4 s’il est défini sur la version 2.  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
