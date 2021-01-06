---
title: Fournisseurs d’événements connus dans .NET
description: Passez en revue les fournisseurs et les événements publiés par le runtime et les bibliothèques .NET.
ms.topic: reference
ms.date: 12/21/2020
ms.openlocfilehash: 03d505f33e300b094958676bb768fb542d828aeb
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97738203"
---
# <a name="well-known-event-providers-in-net"></a>Fournisseurs d’événements connus dans .NET

Le runtime et les bibliothèques .NET écrivent des événements de diagnostic via un certain nombre de fournisseurs d’événements différents. Selon vos besoins de diagnostic, vous pouvez choisir les fournisseurs appropriés à activer. Cet article décrit certains des fournisseurs d’événements les plus couramment utilisés dans le runtime et les bibliothèques .NET.

## <a name="coreclr"></a>CoreCLR

### <a name="microsoft-windows-dotnetruntime-provider"></a>Fournisseur « Microsoft-Windows-DotNETRuntime »

Ce fournisseur émet divers événements à partir du Runtime .NET, y compris GC, Loader, JIT, exception et d’autres événements. Pour en savoir plus sur chaque événement, consultez la [liste des événements du fournisseur du runtime](../../fundamentals/diagnostics/runtime-events.md).

### <a name="microsoft-dotnetcore-sampleprofiler-provider"></a>Fournisseur « Microsoft-DotNETCore-SampleProfiler »

Ce fournisseur est un fournisseur d’événements de Runtime .NET utilisé pour l’échantillonnage de l’UC pour les piles managés. Lorsqu’il est activé, il capture un instantané de la pile d’appels managée de chaque thread toutes les 10 millisecondes. Pour activer cette capture, vous devez spécifier une <xref:System.Diagnostics.Tracing.EventLevel> `Informational` valeur ou une valeur supérieure.

## <a name="framework-libraries"></a>Bibliothèques de framework

### <a name="microsoft-extensions-dependencyinjection-provider"></a>Fournisseur « Microsoft-extensions-DependencyInjection »

Ce fournisseur journalise des informations à partir de DependencyInjection. Le tableau suivant montre les événements consignés par le `Microsoft-Extensions-DependencyInjection` fournisseur :

|Nom d'événement|Level|Description|
|----------|-----|-----------|
|`CallSiteBuilt`|Détaillé (5)|Un site d’appel a été créé.|
|`ServiceResolved`|Détaillé (5)|Un service a été résolu.|
|`ExpressionTreeGenerated`|Détaillé (5)|Une arborescence de l’expression a été générée.|
|`DynamicMethodBuilt`|Détaillé (5)|<xref:System.Reflection.Emit.DynamicMethod>A été généré.|

### <a name="systembuffersarraypooleventsource-provider"></a>Fournisseur « System. buffers. ArrayPoolEventSource »

Ce fournisseur journalise des informations à partir de ArrayPool. Le tableau suivant montre les événements consignés par `ArrayPoolEventSource` :

|Nom d'événement|Level|Description|
|----------|-----|-----------|
|`BufferRented`|Détaillé (5)|Une mémoire tampon est correctement louée.|
|`BufferAllocated`|Informatif (4)|Une mémoire tampon est allouée par le pool.|
|`BufferReturned`|Détaillé (5)|Une mémoire tampon est retournée au pool.|
|`BufferTrimmed`|Informatif (4)|Une mémoire tampon est tentée pour être libérée en raison de la sollicitation de la mémoire ou de l’inactivité.|
|`BufferTrimPoll`|Informatif (4)|Une vérification est effectuée pour découper les tampons.|

### <a name="systemnethttp-provider"></a>Fournisseur « System .net. http »

Ce fournisseur journalise des informations à partir de la pile HTTP. Le tableau suivant montre les événements consignés par le `System.Net.Http` fournisseur :

|Nom d'événement|Level|Description|
|----------|-----|-----------|
|RequestStart|Informatif (4)|Une requête HTTP a démarré.|
|RequestStop|Informatif (4)|Une requête HTTP est terminée.|
|RequestFailed|Erreur (2)|Une requête HTTP a échoué.|
|ConnectionEstablished|Informatif (4)|Une connexion HTTP a été établie.|
|ConnectionClosed|Informatif (4)|Une connexion HTTP a été fermée.|
|RequestLeftQueue|Informatif (4)|Une requête HTTP a quitté la file d’attente des demandes.|
|RequestHeadersStart|Informatif (4)|Une requête HTTP pour l’en-tête a démarré.|
|RequestHeaderStop|Informatif (4)|Une requête HTTP pour l’en-tête est terminée.|
|RequestContentStart|Informatif (4)|Une requête HTTP relative au contenu a démarré.|
|RequestContentStop|Informatif (4)|Une requête HTTP de contenu est terminée.|
|ResponseHeadersStart|Informatif (4)|Une réponse HTTP pour l’en-tête a démarré.|
|ResponseHeaderStop|Informatif (4)|Une réponse HTTP pour l’en-tête est terminée.|
|ResponseContentStart|Informatif (4)|Une réponse HTTP pour le contenu a démarré.|
|ResponseContentStop|Informatif (4)|Une réponse HTTP pour le contenu s’est terminée.|

### <a name="systemnetnameresolution-provider"></a>Fournisseur « System .net. NameResolution »

Ce fournisseur journalise des informations relatives à la résolution de noms de domaine. Le tableau suivant montre les événements consignés par `System.Net.NameResolution` :

|Nom d'événement|Level|Description|
|----------|-----|-----------|
|`ResolutionStart`|Informatif (4)|Une résolution de noms de domaine a démarré.|
|`ResolutionStop`|Informatif (4)|Une résolution de nom de domaine est terminée.|
|`ResolutionFailed`|Informatif (4)|Une résolution de nom de domaine a échoué.|

### <a name="systemnetsockets-provider"></a>Fournisseur « System .net. Sockets »

Ce fournisseur journalise des informations à partir de <xref:System.Net.Sockets.Socket> . Le tableau suivant montre les événements consignés par le `System.Net.Sockets` fournisseur :

|Nom d'événement|Level|Description|
|----------|-----|-----------|
|`ConnectStart`|Informatif (4)|Une tentative de démarrage d’une connexion de socket a démarré.|
|`ConnectStop`|Informatif (4)|Une tentative de démarrage d’une connexion de socket est terminée.|
|`ConnectFailed`|Informatif (4)|Une tentative de démarrage d’une connexion de socket a échoué.|
|`AcceptStart`|Informatif (4)|Une tentative d’acceptation d’une connexion de socket a démarré.|
|`AcceptStop`|Informatif (4)|Une tentative d’acceptation d’une connexion de socket est terminée.|
|`AcceptFailed`|Informatif (4)|Une tentative d’acceptation d’une connexion de socket a échoué.|

### <a name="systemthreadingtaskstpleventsource-provider"></a>Fournisseur « System. Threading. Tasks. TplEventSource »

Ce fournisseur journalise des informations sur la [bibliothèque parallèle de tâches](../../standard/parallel-programming/task-parallel-library-tpl.md), telles que les événements du planificateur de tâches. Le tableau suivant montre les événements consignés par `TplEventSource` :

|Nom d'événement|Mot clé|Level|Description|
|----------|-------|-----|-----------|
|`TaskScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|Informatif (4)|Un <xref:System.Threading.Tasks.Task> est mis en file d’attente dans le planificateur de tâches.|
|`TaskStarted`|`Tasks`(`0x2`)|Informatif (4)|<xref:System.Threading.Tasks.Task>L’exécution d’un a commencé.|
|`TaskCompleted`|`TaskStops`(`0x40`)|Informatif (4)|<xref:System.Threading.Tasks.Task>L’exécution d’un a été terminée.|
|`TaskWaitBegin`|`TaskTransfer`(`0x1`)<br /><br />`TaskWait`(`0x2`)|Informatif (4)|Déclenché lorsqu’une attente implicite ou explicite sur un <xref:System.Threading.Tasks.Task> achèvement a démarré.|
|`TaskWaitEnd`|`Tasks`(`0x2`)|Détaillé (5)|Déclenché lorsque l’attente d’une <xref:System.Threading.Tasks.Task> saisie semi-automatique est retournée.|
|`TaskWaitContinuationStarted`|`Tasks`(`0x2`)|Détaillé (5)|Déclenché lorsque le travail (méthode) associé à un `TaskWaitEnd` est démarré.|
|`TaskWaitContinuationCompleted`|`TaskStops`(`0x40`)|Détaillé (5)|Déclenché lorsque le travail (méthode) associé à un `TaskWaitEnd` est terminé.|
|`AwaitTaskContinuationScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|Informatif (4)|Déclenché lorsque la continuation asynchrone d’un <xref:System.Threading.Tasks.Task> est planifiée.|

## <a name="aspnet-core"></a>ASP.NET Core

ASP.NET Core fournit également plusieurs événements pour vous aider à diagnostiquer les problèmes dans la pile de ASP.NET Core.

Pour en savoir plus sur les événements dans ASP.NET Core et leur utilisation, consultez [journalisation dans .net Core et ASP.net Core](/aspnet/core/fundamentals/logging/).
