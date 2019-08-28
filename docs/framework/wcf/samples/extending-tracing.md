---
title: Extending Tracing
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 957ba3f1fc8c778ebb5b481d329af9906a36fde9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044965"
---
# <a name="extending-tracing"></a>Extending Tracing
Cet exemple montre comment étendre la fonctionnalité de suivi Windows Communication Foundation (WCF) en écrivant des suivis d’activité définis par l’utilisateur dans le code du client et du service. Cela permet à l'utilisateur de créer des activités de suivi et de regrouper les suivis dans des unités de travail logiques. Il est également possible de mettre en corrélation des activités à travers des transferts (au sein du même point de terminaison) et la propagation (sur plusieurs points de terminaison). Dans cet exemple, le suivi est activé à la fois pour le client et pour le service. Pour plus d’informations sur l’activation du suivi dans les fichiers de configuration du client et du service, consultez [suivi et journalisation des messages](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Suivi et propagation d'activité  
 Le suivi d’activité défini par l’utilisateur permet à l’utilisateur de créer ses propres activités de suivi pour regrouper les suivis en unités de travail logiques, mettre en corrélation les activités via les transferts et la propagation, et réduire le coût de performance du suivi WCF (par exemple, le coût de l’espace disque). d’un fichier journal).  
  
### <a name="adding-custom-sources"></a>Ajout de sources personnalisées  
 Les suivis définis par l'utilisateur peuvent être ajoutés à la fois au code du client et du service. L’ajout de sources de suivi aux fichiers de configuration du client ou du service permet d’enregistrer et d’afficher ces suivis personnalisés dans l' [outil Service Trace Viewer (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Le code suivant montre comment ajouter une source de suivi définie par l'utilisateur nommée `ServerCalculatorTraceSource` au fichier de configuration.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a>Mise en corrélation des activités  
 Pour mettre directement en corrélation des activités sur plusieurs points de terminaison, l'attribut `propagateActivity` doit avoir la valeur `true` dans la source du suivi `System.ServiceModel`. En outre, pour propager des traces sans passer par des activités WCF, le suivi d’activité ServiceModel doit être désactivé. C'est ce qu'illustre l'exemple de code suivant.  
  
> [!NOTE]
> La désactivation du suivi d'activité ServiceModel n'équivaut pas à désactiver le niveau de suivi, dénoté par la propriété `switchValue`.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Réduction des coûts de performance  
 Le fait de désactiver `ActivityTracing` dans la source de suivi `System.ServiceModel` génère un fichier de suivi qui contient uniquement les suivis d'activité définis par l'utilisateur, sans inclure les suivis d'activité ServiceModel. Ainsi, le fichier journal est beaucoup moins volumineux. Toutefois, l’opportunité de mettre en corrélation les suivis de traitement WCF est perdue.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de surveillance AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
