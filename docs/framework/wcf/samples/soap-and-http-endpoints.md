---
title: Points de terminaison SOAP et HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: f10b1aa4514aee50c0c0d17cabdb9516a3ca7584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144017"
---
# <a name="soap-and-http-endpoints"></a>Points de terminaison SOAP et HTTP
Cet exemple montre comment implémenter un service basé sur le RPC et l’exposer dans le format SOAP et le format « Plain Old XML » (POX) à l’aide du modèle de programmation Web de WCF. Consultez l’échantillon [basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) pour plus de détails sur la liaison HTTP pour le service. Cet exemple se concentre sur les détails ayant trait à l’exposition du même service sur SOAP et HTTP au moyen de différentes liaisons.  
  
## <a name="demonstrates"></a>Illustre le  
 Exposer un service RPC sur SOAP et HTTP en utilisant WCF.  
  
## <a name="discussion"></a>Discussions  
 Cet exemple se compose de deux composantes : un projet d’application Web (Service) qui contient un service WCF et une application de console (Client) qui invoque les opérations de service à l’aide de liaisons SOAP et HTTP.  
  
 Le service WCF expose 2 `PutData` opérations et`GetData` qui font écho à la chaîne qui a été adoptée comme entrée. Les opérations de service sont annotées avec <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>. Ces attributs contrôlent la projection HTTP de ces opérations. Elles sont aussi annotées avec <xref:System.ServiceModel.OperationContractAttribute>, ce qui permet leur exposition sur des liaisons SOAP. La méthode `PutData` du service lève un <xref:System.ServiceModel.Web.WebFaultException>, qui est renvoyé sur HTTP avec le code d'état HTTP et sur SOAP en tant qu'erreur SOAP.  
  
 Le fichier Web.config configure le service WCF avec 3 points de terminaison :  
  
- le point de terminaison ~/service.svc/mex qui expose les métadonnées du service pour l'accès des clients SOAP ;  
  
- le point de terminaison ~/service.svc/http qui permet aux clients d’accéder au service en utilisant la liaison HTTP ;  
  
- le point de terminaison ~/service.svc/soap qui permet aux clients d’accéder au service en utilisant la liaison SOAP sur HTTP.  
  
 Le point de terminaison HTTP est `webHttp` configuré avec un `helpEnabled` <`true`> point de terminaison standard qui s’est fixé à . Par conséquent, le service expose sous ~/service.svc/http/help une page d'aide XHTML que les clients HTTP peuvent utiliser pour accéder au service.  
  
 Le projet client démontre l’accès au service à l’aide d’un <xref:System.Net.WebClient>proxy SOAP (généré par Add Service **Reference**) et l’accès au service à l’aide de .  
  
 L'exemple se compose d'un service hébergé sur le Web et d'une application console. Lorsque l'application console s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### <a name="to-run-the-sample"></a>Exécution de l'exemple  
  
1. Ouvrez la solution de l'exemple des points de terminaison SOAP et HTTP.  
  
2. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
3. S’il n’est pas déjà ouvert, appuyez sur CTRL-W, S pour ouvrir la fenêtre **Solution Explorer.**  
  
4. De la fenêtre **Solution Explorer,** cliquez à droite sur le projet **Service** et placez le curseur sur l’option de menu **contexte Debug** afin que le menu **Contexte Start New Instance** apparaisse. Cliquez **sur Démarrer nouvelle instance**. Cette opération lance le serveur de développement ASP.NET, qui héberge le service.  
  
5. Depuis les fenêtres Solution Explorer, cliquez à droite sur le projet Client et placez le curseur sur l’option de menu **contexte Debug** afin que le menu **Contexte Start New Instance** apparaisse. Cliquez **sur Démarrer nouvelle instance**.  
  
6. La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML. Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.  
  
7. Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.  
  
8. Appuyez sur une touche quelconque pour arrêter l'application console Client.  
  
9. Appuyez sur MAJ+F5 pour arrêter le débogage du service.  
  
10. Dans la zone de notification Windows, cliquez à droite sur l’icône ASP.NET serveur de développement et **sélectionnez Stop** dans le menu contextuelle.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
