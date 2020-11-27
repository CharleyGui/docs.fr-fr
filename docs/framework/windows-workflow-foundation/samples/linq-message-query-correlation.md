---
title: Corrélation de requête de message LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 83ffc80bd1944681da29e9058de454636aa7405b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291100"
---
# <a name="linq-message-query-correlation"></a>Corrélation de requête de message LINQ

Cet exemple montre comment effectuer une corrélation basée sur le contenu à l’aide d’une implémentation <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisée par opposition au <xref:System.ServiceModel.XPathMessageQuery> fourni par le système.  
  
## <a name="demonstrates"></a>Illustre le  

 <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisé, corrélation basée sur le contenu.  
  
## <a name="discussion"></a>Discussions  

 Cet exemple montre le mode d'extension à partir de la classe de base <xref:System.ServiceModel.Dispatcher.MessageQuery> pour les besoins de la corrélation. L'implémentation personnalisée, `LinqMessageQuery`, permet aux utilisateurs de fournir un XName à rechercher dans le message à l'aide de XLinq. Les données récupérées par la requête sont utilisées pour former la clé de corrélation afin de distribuer des messages à l'instance de workflow appropriée.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP. Pour exécuter cet exemple, des listes de contrôle d’accès d’URL appropriées doivent être ajoutées (pour plus d’informations, consultez [configuration de http et HTTPS](../../wcf/feature-details/configuring-http-and-https.md) ), soit en exécutant Visual Studio en tant qu’administrateur, soit en exécutant la commande suivante à une invite de commandes avec élévation de privilèges pour ajouter les listes de contrôle d’accès appropriées. Vérifiez que vos domaine et nom d'utilisateur sont substitués.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Une fois les listes de contrôle d'accès (ACL) d'URL ajoutées, effectuez les étapes suivantes.  
  
    1. Générez la solution.  
  
    2. Pour définir plusieurs projets de démarrage, cliquez avec le bouton droit sur la solution et sélectionnez **définir les projets de démarrage**. Ajoutez le **service** et le **client** (dans cet ordre) en tant que plusieurs projets de démarrage.  
  
    3. Exécutez l'application. La console cliente affiche un workflow qui envoie une commande et reçoit l'ID de bon de commande, puis confirme par la suite la commande. La fenêtre Service affichera les demandes en cours de traitement.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
