---
title: traçage analytique [WCF]
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 13c66fbe1b59158cb9d2ba3829bb12f1180ad576
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552977"
---
# <a name="wcf-analytic-tracing"></a>traçage analytique [WCF]
Cet exemple montre comment ajouter vos propres événements de suivi dans le flux de suivis analytiques que Windows Communication Foundation (WCF) écrit dans ETW dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] . Les traces analytiques permettent d'obtenir facilement une visibilité de vos services sans que cela se traduise par une lourde pénalité en termes de performances. Cet exemple montre comment utiliser les <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API pour écrire des événements qui s’intègrent aux services WCF.  
  
 Pour plus d’informations sur les <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API, consultez <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> .  
  
 Pour en savoir plus sur le suivi d’événements dans Windows, consultez [améliorer le débogage et le réglage des performances avec ETW](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).  
  
## <a name="disposing-eventprovider"></a>Suppression d'EventProvider  
 Cet exemple utilise la classe <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType>, qui implémente <xref:System.IDisposable?displayProperty=nameWithType>. Lors de l’implémentation du suivi pour un service WCF, il est probable que vous pouvez utiliser les ressources de la <xref:System.Diagnostics.Eventing.EventProvider> durée de vie du service. Pour cette raison, et à des fins de lisibilité, cet exemple ne supprime jamais l'<xref:System.Diagnostics.Eventing.EventProvider> inclus dans un wrapper. Si pour une raison ou une autre, les exigences de votre service diffèrent en matière de suivi et que vous devez supprimer cette ressource, modifiez cet exemple conformément aux meilleures pratiques de suppression de ressources non managées. Pour plus d’informations sur la suppression des ressources non managées, consultez [implémentation d’une méthode dispose](../../../standard/garbage-collection/implementing-dispose.md).  
  
## <a name="self-hosting-vs-web-hosting"></a>Auto-hébergement et hébergement Web  
 Pour les services hébergés sur le Web, les traces analytiques de WCF fournissent un champ, appelé « HostReference », qui est utilisé pour identifier le service qui émet les traces. Les traces utilisateur extensibles peuvent participer à ce modèle et cet exemple en illustre les meilleures pratiques. Le format d’une référence d’hôte Web lorsque le caractère « &#124; » du canal apparaît réellement dans la chaîne résultante peut être l’un des éléments suivants :  
  
- Si l'application ne se situe pas à la racine.  
  
     \<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
- Si l'application se situe à la racine.  
  
     \<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
 Pour les services auto-hébergés, les traces analytiques de WCF ne remplissent pas le champ « HostReference ». La classe `WCFUserEventProvider` de cet exemple se comporte de manière cohérente lorsqu'elle est utilisée par un service auto-hébergé.  
  
## <a name="custom-event-details"></a>Informations sur l'événement personnalisé  
 Le manifeste du fournisseur d’événements ETW de WCF définit trois événements qui sont conçus pour être émis par les auteurs de service WCF à partir du code de service. Le tableau suivant détaille ces trois événements.  
  
|Événement|Description|ID de l’événement|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Émettez cet événement lorsqu'un fait remarquable, qui n'est pas un problème, se produit dans votre service. Par exemple, vous pouvez émettre un événement après qu'un appel à une base de données a abouti.|301|  
|UserDefinedWarningOccurred|Émettez cet événement lorsqu'un problème susceptible d'aboutir à un échec se produit. Par exemple, vous pouvez émettre un événement d'avertissement lorsqu'un appel à une base de données a échoué, mais que vous avez pu recourir à une banque de données redondante.|302|  
|UserDefinedErrorOccurred|Émettez cet événement lorsque votre service ne se comporte pas comme prévu. Par exemple, vous pouvez émettre un événement si un appel à une base de données a échoué et que vous n'avez pas pu récupérer les données ailleurs.|303|  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1. À l’aide de Visual Studio 2012, ouvrez le fichier solution WCFAnalyticTracingExtensibility. sln.  
  
2. Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3. Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
     Dans le navigateur Web, cliquez sur **Calculator. svc**. L'URI du document WSDL du service doit s'afficher dans le navigateur. Copiez cet URI.  
  
4. Exécutez le client test WCF (WcfTestClient.exe).  
  
     Le client test WCF (WcfTestClient.exe) se trouve à l’adresse `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe` . Le répertoire d’installation par défaut de Visual Studio 2012 est `C:\Program Files\Microsoft Visual Studio 10.0` .  
  
5. Dans le client test WCF, ajoutez le service en sélectionnant **fichier**, puis **Ajouter un service**.  
  
     Ajoutez l'adresse du point de terminaison dans la zone d'entrée.  
  
6. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
     Le service ICalculator est ajouté dans le volet gauche sous **mes projets de service**.  
  
7. Ouvrez l'application Observateur d'événements.  
  
     Avant d’appeler le service, démarrez observateur d’événements et assurez-vous que le journal des événements écoute les événements de suivi émis à partir du service WCF.  
  
8. Dans le menu **Démarrer** , sélectionnez **Outils d’administration**, puis **Observateur d’événements**. Activez les journaux d' **analyse** et de **débogage** .  
  
9. Dans l’arborescence de observateur d’événements, accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis serveur d’applications **-applications**. Cliquez avec le bouton droit sur **serveur d’applications-applications**, sélectionnez **affichage**, puis **Affichez les journaux d’analyse et de débogage**.  
  
     Assurez-vous que l’option **afficher les journaux d’analyse et de débogage** est activée. Activez le journal d' **analyse** .  
  
     Dans l’arborescence de observateur d’événements, accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, **serveur d’applications-applications**, puis **analysez**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **activer le journal**.  
  
10. Testez le service à l'aide du client test WCF.  
  
    1. Dans le client test WCF, double-cliquez sur **Add ()** sous le nœud de service ICalculator.  
  
         La méthode **Add ()** s’affiche dans le volet droit avec deux paramètres.  
  
    2. Tapez 2 pour le premier paramètre et 3 pour le deuxième.  
  
    3. Cliquez sur **appeler** pour appeler la méthode.  
  
11. Accédez à la fenêtre de **Observateur d’événements** que vous avez déjà ouverte. Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, serveur d’applications **-applications**.  
  
12. Cliquez avec le bouton droit sur le nœud **analyse** et sélectionnez **Actualiser**.  
  
     Les événements s'affichent dans le volet droit.  
  
13. Trouvez l'événement avec l'ID 303 et double-cliquez dessus pour l'ouvrir et en inspecter le contenu.  
  
     Cet événement a été émis par la `Add()` méthode du service ICalculator et a une charge utile égale à « 2 + 3 = 5 ».  
  
#### <a name="to-clean-up-optional"></a>Pour nettoyer (facultatif)  
  
1. Ouvrez l’ **Observateur d’événements**.  
  
2. Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis **application-serveur-applications**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **désactiver le journal**.  
  
3. Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, **Application-Server-applications**, puis **analyse**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **effacer le journal**.  
  
4. Cliquez sur **Effacer** pour effacer les événements.  
  
## <a name="known-issue"></a>Problème connu  
 Il existe un problème connu dans le **Observateur d’événements** où il peut ne pas être en mesure de décoder les événements ETW. Vous pouvez voir un message d’erreur indiquant : «la description de l’ID \<id> d’événement de la source Microsoft-Windows-serveur d’applications-applications est introuvable. Le composant qui déclenche cet événement n’est pas installé sur votre ordinateur local, ou l’installation est endommagée. Vous pouvez installer ou réparer le composant sur l’ordinateur local.» Si vous rencontrez cette erreur, sélectionnez **Actualiser** dans le menu **actions** . Le décodage de l'événement doit ensuite s'effectuer correctement.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))
