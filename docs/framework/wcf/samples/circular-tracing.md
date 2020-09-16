---
title: Circular Tracing
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: d9af1f18a507a79c9c287393652e65dcb3372444
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552516"
---
# <a name="circular-tracing"></a>Circular Tracing

Cet exemple montre l'implémentation d'un écouteur de suivis mis en mémoire tampon circulaire. L'un des scénarios courants pour les services de production consiste à disposer de services disponibles pendant de longues périodes et à activer la journalisation du suivi à un faible niveau. Ces services consomment beaucoup d'espace disque. Lors du dépannage d'un service, les données les plus récentes du journal de suivi s'avèrent pertinentes pour la résolution d'un problème. Cet exemple présente l'implémentation d'un écouteur de suivis mis en mémoire tampon circulaire dans lequel seules les suivis les plus récents sont conservés sur le disque jusqu'à un nombre de donnés configurable. Cet exemple est basé sur le [prise en main](getting-started-sample.md) et comprend un écouteur de traçage personnalisé.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Cet exemple suppose que vous êtes familiarisé avec l’exemple de [suivi et de journalisation des messages](tracing-and-message-logging.md) et que vous avez lu la documentation fournie pour l’exemple [suivi et journalisation des messages](tracing-and-message-logging.md) .

## <a name="circular-buffer-trace-listener"></a>Écouteur de suivis mis en mémoire tampon circulaire

Le concept sous-jacent de l'implémentation de l'écouteur de suivis mis en mémoire tampon circulaire consiste à disposer de deux fichiers pouvant stocker chacun jusqu'à la moitié du nombre total de données du journal de suivi souhaitées. L'écouteur crée un fichier et écrit dans celui-ci jusqu'à ce qu'il atteigne la limite fixée à la moitié de la taille des données, stade à partir duquel il bascule sur un deuxième fichier. Lorsque l'écouteur atteint la limite pour deuxième fichier il écrase le premier fichier avec de nouveaux suivis.

Cet écouteur est dérivé de `XmlWriteTraceListener` et permet l’affichage des journaux à l’aide de l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md). Si vous souhaitez consulter les journaux, vous pouvez recombiner les deux fichiers journaux facilement en les ouvrant en même temps dans l'outil Service Trace Viewer. Cet outil trie automatiquement les suivis afin qu'ils apparaissent dans l'ordre correct.

## <a name="configuration"></a>Configuration

Un service peut être configuré pour utiliser l'écouteur de suivis mis en mémoire tampon circulaire en ajoutant le code suivant pour un écouteur et des éléments sources. La taille de fichier maximale est spécifiée à l'aide de l'attribut `maxFileSizeKB` dans la configuration de l'écouteur de suivis circulaire. Cela est illustré dans le code suivant :

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">
      <listeners>
        <add name="CircularTraceListener" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />
  </sharedListeners>
  <trace autoflush="true" />
</system.diagnostics>
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))
