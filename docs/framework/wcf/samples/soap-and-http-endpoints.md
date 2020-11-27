---
title: Points de terminaison SOAP et HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 9e7ce32a0f5a2f37294db57659e2b30b364bef24
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268259"
---
# <a name="soap-and-http-endpoints"></a>Points de terminaison SOAP et HTTP

Cet exemple montre comment implémenter un service basé sur RPC et l’exposer au format SOAP et au format POX (Plain Old XML) à l’aide du modèle de programmation Web WCF. Pour plus d’informations sur la liaison HTTP pour le service, consultez l’exemple de [service http de base](basic-http-service.md) . Cet exemple se concentre sur les détails ayant trait à l’exposition du même service sur SOAP et HTTP au moyen de différentes liaisons.  
  
## <a name="demonstrates"></a>Illustre le  

 Exposition d’un service RPC sur SOAP et HTTP à l’aide de WCF.  
  
## <a name="discussion"></a>Discussions  

 Cet exemple se compose de deux composants : un projet d’application Web (service) qui contient un service WCF et une application console (client) qui appelle des opérations de service à l’aide de liaisons SOAP et HTTP.  
  
 Le service WCF expose 2 opérations, `GetData` et, `PutData` qui répercutent la chaîne passée comme entrée. Les opérations de service sont annotées avec <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>. Ces attributs contrôlent la projection HTTP de ces opérations. Elles sont aussi annotées avec <xref:System.ServiceModel.OperationContractAttribute>, ce qui permet leur exposition sur des liaisons SOAP. La méthode `PutData` du service lève un <xref:System.ServiceModel.Web.WebFaultException>, qui est renvoyé sur HTTP avec le code d'état HTTP et sur SOAP en tant qu'erreur SOAP.  
  
 Le fichier Web.config configure le service WCF avec 3 points de terminaison :  
  
- le point de terminaison ~/service.svc/mex qui expose les métadonnées du service pour l'accès des clients SOAP ;  
  
- le point de terminaison ~/service.svc/http qui permet aux clients d’accéder au service en utilisant la liaison HTTP ;  
  
- le point de terminaison ~/service.svc/soap qui permet aux clients d’accéder au service en utilisant la liaison SOAP sur HTTP.  
  
 Le point de terminaison HTTP est configuré avec un <`webHttp`> point de terminaison standard qui a la `helpEnabled` valeur `true` . Par conséquent, le service expose sous ~/service.svc/http/help une page d'aide XHTML que les clients HTTP peuvent utiliser pour accéder au service.  
  
 Le projet client illustre l’accès au service à l’aide d’un proxy SOAP (généré via **Ajouter une référence de service**) et l’accès au service à l’aide de <xref:System.Net.WebClient> .  
  
 L'exemple se compose d'un service hébergé sur le Web et d'une application console. Lorsque l'application console s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### <a name="to-run-the-sample"></a>Exécution de l'exemple  
  
1. Ouvrez la solution de l'exemple des points de terminaison SOAP et HTTP.  
  
2. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
3. S’il n’est pas déjà ouvert, appuyez sur CTRL + W, S pour ouvrir la fenêtre **Explorateur de solutions** .  
  
4. Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le projet de **service** et placez le curseur sur l’option de menu contextuel **débogage** pour afficher le menu contextuel **Démarrer une nouvelle instance** . Cliquez sur **Démarrer une nouvelle instance**. Cette opération lance le serveur de développement ASP.NET, qui héberge le service.  
  
5. Dans le Explorateur de solutions Windows, cliquez avec le bouton droit sur le projet client et placez le curseur sur l’option de menu contextuel **débogage** pour afficher le menu contextuel **Démarrer une nouvelle instance** . Cliquez sur **Démarrer une nouvelle instance**.  
  
6. La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML. Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.  
  
7. Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.  
  
8. Appuyez sur une touche quelconque pour arrêter l'application console Client.  
  
9. Appuyez sur MAJ+F5 pour arrêter le débogage du service.  
  
10. Dans la zone de notification Windows, cliquez avec le bouton droit sur l’icône du serveur de développement ASP.NET et sélectionnez **arrêter** dans le menu contextuel.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
