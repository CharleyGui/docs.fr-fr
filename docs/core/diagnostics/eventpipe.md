---
title: Présentation de EventPipe
description: Découvrez EventPipe et comment l’utiliser pour effectuer le suivi de vos applications .NET afin de diagnostiquer les problèmes de performances.
ms.date: 11/09/2020
ms.topic: overview
ms.openlocfilehash: 00378c4f409b307afa9183e40de6078cdafd3ae7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820616"
---
# <a name="eventpipe"></a>EventPipe

EventPipe est un composant d’exécution qui peut être utilisé pour collecter des données de suivi, comme ETW ou LTTng. L’objectif de EventPipe est de permettre aux développeurs .NET de suivre facilement leurs applications .NET sans avoir à s’appuyer sur des composants natifs du système d’exploitation spécifiques à la plateforme, tels que ETW ou LTTng.

EventPipe est le mécanisme qui sous-tend un grand nombre d’outils de diagnostic et qui peut être utilisé pour consommer des événements émis par le runtime ainsi que des événements personnalisés écrits avec [EventSource](xref:System.Diagnostics.Tracing.EventSource).

Cet article est une vue d’ensemble de EventPipe qui décrit quand et comment utiliser EventPipe et comment le configurer en fonction de vos besoins.

## <a name="eventpipe-basics"></a>Notions de base de EventPipe

EventPipe agrège les événements émis par les composants d’exécution (par exemple, le compilateur juste-à-temps ou le garbage collector) et les événements écrits à partir d’instances [EventSource](xref:System.Diagnostics.Tracing.EventSource) dans les bibliothèques et le code utilisateur.

Les événements sont ensuite sérialisés et peuvent être écrits directement dans un fichier ou utilisés par le biais d’un port de diagnostic. Sur Windows, les ports de diagnostic sont implémentés en tant que `NamedPipe` s. Sur les plateformes autres que Windows, telles que Linux ou macOS, elles sont implémentées à l’aide de sockets de domaine UNIX. Pour plus d’informations sur le port de diagnostic et sur la manière d’interagir avec lui via son protocole de communication interprocessus personnalisé, consultez la [documentation relative au protocole IPC pour les diagnostics](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).

EventPipe écrit ensuite les événements sérialisés au `.nettrace` format de fichier sous forme de flux via des ports de diagnostic ou directement dans un fichier. Pour en savoir plus sur le format de sérialisation EventPipe, reportez-vous à la [documentation de format EventPipe](https://github.com/microsoft/perfview/blob/master/src/TraceEvent/EventPipe/EventPipeFormat.md).

## <a name="eventpipe-vs-etwlttng"></a>EventPipe et ETW/LTTng

EventPipe fait partie du .NET Runtime (CoreCLR) et est conçu pour fonctionner de la même façon sur toutes les plateformes prises en charge par .NET Core. Cela permet aux outils de suivi basés sur EventPipe, tels que `dotnet-counters` , `dotnet-gcdump` et `dotnet-trace` , de fonctionner de manière transparente entre les plateformes.

Toutefois, étant donné que EventPipe est un composant d’exécution intégré, sa portée est limitée au code managé et au runtime lui-même. EventPipe ne peut pas être utilisé pour le suivi de certains événements de niveau inférieur, tels que la résolution de la pile de code natif ou l’obtention de différents événements de noyau. Si vous utilisez l’interopérabilité C/C++ dans votre application ou si vous souhaitez suivre le runtime lui-même (qui est écrit en C++), ou si vous souhaitez des diagnostics plus approfondis dans le comportement de l’application qui requiert des événements de noyau (c’est-à-dire des événements de basculement de contexte de thread natif), vous devez utiliser ETW ou [perf/LTTng](./trace-perfcollect-lttng.md).

Une autre différence majeure entre EventPipe et ETW/LTTng est l’exigence d’un privilège d’administration/racine. Pour effectuer le suivi d’une application à l’aide de ETW ou LTTng, vous devez être administrateur/racine. À l’aide de EventPipe, vous pouvez tracer des applications tant que le traceur (par exemple, `dotnet-trace` ) est exécuté en tant qu’utilisateur qui a lancé l’application.

Le tableau suivant résume les différences entre EventPipe et ETW/LTTng.

|Fonctionnalité|EventPipe|ETW|LTTng|
|-------|---------|---|-----------|
|Système multiplateforme|Oui|Non (uniquement sur Windows)|Non (uniquement sur les distributions Linux pris en charge)|
|Exiger un privilège d’administrateur/racine|Non|Oui|Oui|
|Peut recevoir des événements du système d’exploitation/noyau|Non|Oui|Oui|
|Peut résoudre les piles natifs|Non|Oui|Oui|

## <a name="use-eventpipe-to-trace-your-net-application"></a>Utiliser EventPipe pour tracer votre application .NET

Vous pouvez utiliser EventPipe pour effectuer le suivi de votre application .NET de plusieurs façons :

* Utilisez l’un des [outils de diagnostic](#tools-that-use-eventpipe) basés sur EventPipe.

* Utilisez la bibliothèque [Microsoft. Diagnostics. Netcore. client](https://github.com/dotnet/diagnostics/blob/master/documentation/diagnostics-client-library-instructions.md) pour écrire votre propre outil afin de configurer et de démarrer vous-même les sessions EventPipe.

* Utilisez des [variables d’environnement](#trace-using-environment-variables) pour démarrer EventPipe.

Une fois que vous avez créé un `nettrace` fichier qui contient vos événements EventPipe, vous pouvez afficher le fichier dans [`PerfView`](https://github.com/Microsoft/perfview#perfview-overview) ou Visual Studio. Sur les plateformes non-Windows, vous pouvez convertir le `nettrace` fichier au `speedscope` format de suivi ou à `Chromium` l’aide de la [`dotnet-trace convert`](./dotnet-trace.md#dotnet-trace-convert) commande et l’afficher avec [`speedscope`](https://www.speedscope.app/) ou chrome devtools.

Vous pouvez également analyser les traces EventPipe par programmation avec [TraceEvent](https://github.com/Microsoft/perfview/blob/master/documentation/TraceEvent/TraceEventLibrary.md).

### <a name="tools-that-use-eventpipe"></a>Outils qui utilisent EventPipe

Il s’agit du moyen le plus simple d’utiliser EventPipe pour tracer votre application. Pour en savoir plus sur l’utilisation de chacun de ces outils, reportez-vous à la documentation de chaque outil.

* [dotnet-Counters](./dotnet-counters.md) vous permet de surveiller et de collecter différentes mesures émises par le Runtime .net et les bibliothèques de base, ainsi que des métriques personnalisées que vous pouvez écrire.

* [dotnet-gcdump](./dotnet-gcdump.md) vous permet de collecter les vidages de tas GC des processus en direct pour analyser le tas managé d’une application.

* [dotnet-trace](./dotnet-trace.md) vous permet de collecter des traces d’applications pour analyser les performances.

## <a name="trace-using-environment-variables"></a>Suivi à l’aide de variables d’environnement

Le mécanisme préféré pour l’utilisation de EventPipe consiste à utiliser `dotnet-trace` ou la `Microsoft.Diagnostics.NETCore.Client` bibliothèque.

Toutefois, vous pouvez utiliser les variables d’environnement suivantes pour configurer une session EventPipe sur une application et faire en sorte qu’elle écrit directement la trace dans un fichier. Pour arrêter le suivi, quittez l’application.

* `COMPlus_EnableEventPipe`: Définissez cette valeur sur `1` pour démarrer une session EventPipe qui écrit directement dans un fichier. La valeur par défaut est `0`.

* `COMPlus_EventPipeOutputPath`: Chemin d’accès au fichier de trace EventPipe de sortie lorsqu’il est configuré pour s’exécuter via `COMPlus_EnableEventPipe` . La valeur par défaut est `trace.nettrace` , qui sera créée dans le répertoire à partir duquel l’application s’exécute.

* `COMPlus_CircularBufferMB`: Taille de la mémoire tampon interne utilisée par EventPipe lorsqu’elle est configurée pour s’exécuter via `COMPlus_EnableEventPipe` .

* `COMPlus_EventPipeConfig`: Définit la configuration de session EventPipe lors du démarrage d’une session EventPipe avec `COMPlus_EnableEventPipe` .

  La syntaxe est la suivante :

  `<provider>:<keyword>:<level>`

  Vous pouvez également spécifier plusieurs fournisseurs en les concaténant à l’aide d’une virgule :

  `<provider1>:<keyword1>:<level1>,<provider2>:<keyword2>:<level2>`

  Si cette variable d’environnement n’est pas définie mais que EventPipe est activé par `COMPlus_EnableEventPipe` , elle démarre le suivi en activant les fournisseurs suivants avec les mots clés et les niveaux suivants :

  - `Microsoft-Windows-DotNETRuntime:4c14fccbd:5`
  - `Microsoft-Windows-DotNETRuntimePrivate:4002000b:5`
  - `Microsoft-DotNETCore-SampleProfiler:0:5`
