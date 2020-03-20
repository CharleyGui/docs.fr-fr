---
title: Corrélation de requête de message LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 507001b165efdcbe7c1e27a07749dbe2eafb468f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182806"
---
# <a name="linq-message-query-correlation"></a>Corrélation de requête de message LINQ
Cet exemple montre comment effectuer une corrélation basée sur le contenu à l’aide d’une implémentation <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisée par opposition au <xref:System.ServiceModel.XPathMessageQuery> fourni par le système.  
  
## <a name="demonstrates"></a>Illustre le  
 <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisé, corrélation basée sur le contenu.  
  
## <a name="discussion"></a>Discussions  
 Cet exemple montre le mode d'extension à partir de la classe de base <xref:System.ServiceModel.Dispatcher.MessageQuery> pour les besoins de la corrélation. L'implémentation personnalisée, `LinqMessageQuery`, permet aux utilisateurs de fournir un XName à rechercher dans le message à l'aide de XLinq. Les données récupérées par la requête sont utilisées pour former la clé de corrélation afin de distribuer des messages à l'instance de workflow appropriée.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP. Pour exécuter cet exemple, des URL appropriées doivent être ajoutées (voir [Configurer HTTP et HTTPS](../../wcf/feature-details/configuring-http-and-https.md) pour plus de détails), soit en exécutant Visual Studio en tant qu’administrateur, soit en exécutant la commande suivante à une invite élevée pour ajouter les ACL appropriés. Vérifiez que vos domaine et nom d'utilisateur sont substitués.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Une fois les listes de contrôle d'accès (ACL) d'URL ajoutées, effectuez les étapes suivantes.  
  
    1. Générez la solution.  
  
    2. Définissez plusieurs projets de démarrage en cliquant à droite sur la solution et en sélectionnant **Set Startup Projects**. Ajoutez **service** et **client** (dans cet ordre) comme plusieurs projets de démarrage.  
  
    3. Exécutez l'application. La console cliente affiche un workflow qui envoie une commande et reçoit l'ID de bon de commande, puis confirme par la suite la commande. La fenêtre Service affichera les demandes en cours de traitement.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
