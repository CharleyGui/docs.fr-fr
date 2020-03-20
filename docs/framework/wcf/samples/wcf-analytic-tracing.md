---
title: traçage analytique [WCF]
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: ef636a672d9384e8e3d658f0488cfaadb8d293e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183216"
---
# <a name="wcf-analytic-tracing"></a>traçage analytique [WCF]
Cet exemple montre comment ajouter vos propres événements de traçage dans le flux de traces [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]analytiques que Windows Communication Foundation (WCF) écrit à ETW dans . Les traces analytiques permettent d'obtenir facilement une visibilité de vos services sans que cela se traduise par une lourde pénalité en termes de performances. Cet exemple montre comment <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> utiliser les API pour écrire des événements qui s’intègrent aux services WCF.  
  
 Pour plus d’informations sur les <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API, voir <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Pour en savoir plus sur le traçage des événements dans Windows, voir [Améliorer le débugging et le réglage des performances avec ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).  
  
## <a name="disposing-eventprovider"></a>Suppression d'EventProvider  
 Cet exemple utilise la classe <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType>, qui implémente <xref:System.IDisposable?displayProperty=nameWithType>. Lors de la mise en œuvre de la <xref:System.Diagnostics.Eventing.EventProvider>recherche pour un service WCF, il est probable que vous pouvez utiliser les ressources de «pour la durée de vie du service. Pour cette raison, et à des fins de lisibilité, cet exemple ne supprime jamais l'<xref:System.Diagnostics.Eventing.EventProvider> inclus dans un wrapper. Si pour une raison ou une autre, les exigences de votre service diffèrent en matière de suivi et que vous devez supprimer cette ressource, modifiez cet exemple conformément aux meilleures pratiques de suppression de ressources non managées. Pour plus d’informations sur l’élimination des ressources non gestions, voir [La mise en œuvre d’une méthode de disposer](https://docs.microsoft.com/dotnet/standard/garbage-collection/implementing-dispose).  
  
## <a name="self-hosting-vs-web-hosting"></a>Auto-hébergement et hébergement Web  
 Pour les services hébergés sur le Web, les traces analytiques de WCF fournissent un champ, appelé «HostReference», qui est utilisé pour identifier le service qui émet les traces. Les traces utilisateur extensibles peuvent participer à ce modèle et cet exemple en illustre les meilleures pratiques. Le format d’une référence d’hôte Web lorsque le caractère « &#124; » de pipe apparaît réellement dans la chaîne résultante peut être n’importe lequel des éléments suivants :  
  
- Si l'application ne se situe pas à la racine.  
  
     \<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
- Si l'application se situe à la racine.  
  
     \<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
 Pour les services auto-hébergés, les traces analytiques de WCF ne peuplent pas le champ «HostReference». La classe `WCFUserEventProvider` de cet exemple se comporte de manière cohérente lorsqu'elle est utilisée par un service auto-hébergé.  
  
## <a name="custom-event-details"></a>Informations sur l'événement personnalisé  
 Le manifeste ETW Event Provider de WCF définit trois événements qui sont conçus pour être émis par les auteurs de services WCF à partir du code de service. Le tableau suivant détaille ces trois événements.  
  
|Événement|Description|ID de l’événement|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Émettez cet événement lorsqu'un fait remarquable, qui n'est pas un problème, se produit dans votre service. Par exemple, vous pouvez émettre un événement après qu'un appel à une base de données a abouti.|301|  
|UserDefinedWarningOccurred|Émettez cet événement lorsqu'un problème susceptible d'aboutir à un échec se produit. Par exemple, vous pouvez émettre un événement d'avertissement lorsqu'un appel à une base de données a échoué, mais que vous avez pu recourir à une banque de données redondante.|302|  
|UserDefinedErrorOccurred|Émettez cet événement lorsque votre service ne se comporte pas comme prévu. Par exemple, vous pouvez émettre un événement si un appel à une base de données a échoué et que vous n'avez pas pu récupérer les données ailleurs.|303|  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1. À l’aide de Visual Studio 2012, ouvrez le fichier de solution WCFAnalyticTracingExtensibility.sln.  
  
2. Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3. Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
     Dans le navigateur Web, cliquez sur **Calculator.svc**. L'URI du document WSDL du service doit s'afficher dans le navigateur. Copiez cet URI.  
  
4. Exécuter le client de test WCF (WcfTestClient.exe).  
  
     Le client de test WCF (WcfTestClient.exe) est situé à `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`. Le par défaut Visual Studio 2012 installer dir est `C:\Program Files\Microsoft Visual Studio 10.0`.  
  
5. Au sein du client de test WCF, ajoutez le service en sélectionnant **Le fichier,** puis **ajoutez le service**.  
  
     Ajoutez l'adresse du point de terminaison dans la zone d'entrée.  
  
6. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
     Le service ICalculator est ajouté dans la vitre gauche dans **my Service Projects**.  
  
7. Ouvrez l'application Observateur d'événements.  
  
     Avant d’invoquer le service, commencez Event Viewer et assurez-vous que le journal de l’événement est à l’écoute des événements de suivi émis par le service WCF.  
  
8. Du menu **Démarrer,** sélectionnez **des outils administratifs,** puis **Event Viewer**. Activez les journaux **Analytic** et **Debug.**  
  
9. Dans la vue d’arbre dans Event Viewer, naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application Server-Applications**. Application à clic droit **Server-Applications**, sélectionnez **View**, puis **Afficher les journaux Analytiques et Debug**.  
  
     Assurez-vous que l’option **Afficher l’analyse et les journaux Debug** est vérifiée. Activez le journal **Analytic.**  
  
     Dans la vue d’arbre dans Event Viewer, naviguez vers **Event Viewer**, **Applications et Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**, puis **Analytic**. Cliquez à droite **Analytic** et **sélectionnez Active Log**.  
  
10. Testez le service à l'aide du client test WCF.  
  
    1. Dans le client de test WCF, double clic **Add()** sous le nœud de service ICalculator.  
  
         La méthode **Add()** apparaît dans la vitre droite avec deux paramètres.  
  
    2. Tapez 2 pour le premier paramètre et 3 pour le deuxième.  
  
    3. Cliquez **sur Invoke** pour invoquer la méthode.  
  
11. Rendez-vous à la fenêtre **Event Viewer** que vous avez déjà ouverte. Naviguez vers **Event Viewer**, Applications and **Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.  
  
12. Cliquez à droite sur le nœud **Analytic** et **sélectionnez Refresh**.  
  
     Les événements s'affichent dans le volet droit.  
  
13. Trouvez l'événement avec l'ID 303 et double-cliquez dessus pour l'ouvrir et en inspecter le contenu.  
  
     Cet événement a été `Add()` émis par la méthode du service ICalculator et a une charge utile égale à "2-3-5".  
  
#### <a name="to-clean-up-optional"></a>Pour nettoyer (facultatif)  
  
1. Ouvrez l’ **Observateur d’événements**.  
  
2. Naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application-Server-Applications**. Cliquez à droite **Analytic** et sélectionnez **Disable Log**.  
  
3. Naviguez vers **Event Viewer**, Applications and **Services Logs**, **Microsoft**, **Windows**, **Application-Server-Applications**, puis **Analytic**. Cliquez à droite **Analytic** et sélectionnez **Clear Log**.  
  
4. Cliquez **sur Clear** pour effacer les événements.  
  
## <a name="known-issue"></a>Problème connu  
 Il y a un problème connu dans le **Visual Event** où il peut ne pas décoder les événements ETW. Vous pouvez voir un message d’erreur qui \<dit: "La description pour l’id d’événement> de la source Microsoft-Windows-Application Server-Applications ne peut pas être trouvé. Le composant qui déclenche cet événement n’est pas installé sur votre ordinateur local, ou l’installation est endommagée. Vous pouvez installer ou réparer le composant sur l’ordinateur local. Si vous rencontrez cette erreur, **sélectionnez Refresh** dans le menu **Actions.** Le décodage de l'événement doit ensuite s'effectuer correctement.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
