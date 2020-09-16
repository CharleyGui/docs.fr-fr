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
# <a name="circular-tracing"></a><span data-ttu-id="adc6d-102">Circular Tracing</span><span class="sxs-lookup"><span data-stu-id="adc6d-102">Circular Tracing</span></span>

<span data-ttu-id="adc6d-103">Cet exemple montre l'implémentation d'un écouteur de suivis mis en mémoire tampon circulaire.</span><span class="sxs-lookup"><span data-stu-id="adc6d-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="adc6d-104">L'un des scénarios courants pour les services de production consiste à disposer de services disponibles pendant de longues périodes et à activer la journalisation du suivi à un faible niveau.</span><span class="sxs-lookup"><span data-stu-id="adc6d-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="adc6d-105">Ces services consomment beaucoup d'espace disque.</span><span class="sxs-lookup"><span data-stu-id="adc6d-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="adc6d-106">Lors du dépannage d'un service, les données les plus récentes du journal de suivi s'avèrent pertinentes pour la résolution d'un problème.</span><span class="sxs-lookup"><span data-stu-id="adc6d-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="adc6d-107">Cet exemple présente l'implémentation d'un écouteur de suivis mis en mémoire tampon circulaire dans lequel seules les suivis les plus récents sont conservés sur le disque jusqu'à un nombre de donnés configurable.</span><span class="sxs-lookup"><span data-stu-id="adc6d-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="adc6d-108">Cet exemple est basé sur le [prise en main](getting-started-sample.md) et comprend un écouteur de traçage personnalisé.</span><span class="sxs-lookup"><span data-stu-id="adc6d-108">This sample is based on the [Getting Started](getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="adc6d-109">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="adc6d-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="adc6d-110">Cet exemple suppose que vous êtes familiarisé avec l’exemple de [suivi et de journalisation des messages](tracing-and-message-logging.md) et que vous avez lu la documentation fournie pour l’exemple [suivi et journalisation des messages](tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="adc6d-110">This sample assumes that you are familiar with the [Tracing and Message Logging](tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="adc6d-111">Écouteur de suivis mis en mémoire tampon circulaire</span><span class="sxs-lookup"><span data-stu-id="adc6d-111">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="adc6d-112">Le concept sous-jacent de l'implémentation de l'écouteur de suivis mis en mémoire tampon circulaire consiste à disposer de deux fichiers pouvant stocker chacun jusqu'à la moitié du nombre total de données du journal de suivi souhaitées.</span><span class="sxs-lookup"><span data-stu-id="adc6d-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="adc6d-113">L'écouteur crée un fichier et écrit dans celui-ci jusqu'à ce qu'il atteigne la limite fixée à la moitié de la taille des données, stade à partir duquel il bascule sur un deuxième fichier.</span><span class="sxs-lookup"><span data-stu-id="adc6d-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="adc6d-114">Lorsque l'écouteur atteint la limite pour deuxième fichier il écrase le premier fichier avec de nouveaux suivis.</span><span class="sxs-lookup"><span data-stu-id="adc6d-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="adc6d-115">Cet écouteur est dérivé de `XmlWriteTraceListener` et permet l’affichage des journaux à l’aide de l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="adc6d-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="adc6d-116">Si vous souhaitez consulter les journaux, vous pouvez recombiner les deux fichiers journaux facilement en les ouvrant en même temps dans l'outil Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="adc6d-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="adc6d-117">Cet outil trie automatiquement les suivis afin qu'ils apparaissent dans l'ordre correct.</span><span class="sxs-lookup"><span data-stu-id="adc6d-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="adc6d-118">Configuration</span><span class="sxs-lookup"><span data-stu-id="adc6d-118">Configuration</span></span>

<span data-ttu-id="adc6d-119">Un service peut être configuré pour utiliser l'écouteur de suivis mis en mémoire tampon circulaire en ajoutant le code suivant pour un écouteur et des éléments sources.</span><span class="sxs-lookup"><span data-stu-id="adc6d-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="adc6d-120">La taille de fichier maximale est spécifiée à l'aide de l'attribut `maxFileSizeKB` dans la configuration de l'écouteur de suivis circulaire.</span><span class="sxs-lookup"><span data-stu-id="adc6d-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="adc6d-121">Cela est illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="adc6d-121">This is demonstrated in the following code.</span></span>

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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="adc6d-122">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="adc6d-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="adc6d-123">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="adc6d-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="adc6d-124">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="adc6d-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="adc6d-125">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="adc6d-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="adc6d-126">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="adc6d-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="adc6d-127">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="adc6d-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="adc6d-128">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="adc6d-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="adc6d-129">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="adc6d-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="adc6d-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adc6d-130">See also</span></span>

- <span data-ttu-id="adc6d-131">[Exemples d'analyse AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="adc6d-131">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
