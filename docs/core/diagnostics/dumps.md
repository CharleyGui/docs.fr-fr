---
title: Dumps-.NET
description: Introduction aux dumps dans .NET.
ms.date: 10/12/2020
ms.openlocfilehash: 7a4c7bf54b3e9ea43e685eafbd00b4a373326520
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764940"
---
# <a name="dumps"></a>Vidages

Un dump est un fichier qui contient un instantané du processus au moment de sa création et peut être utile pour examiner l’état de votre application. Les dumps peuvent être utilisés pour déboguer votre application .NET lorsqu’il est difficile de joindre un débogueur à celui-ci, comme les environnements de production ou CI. L’utilisation de dumps vous permet de capturer l’état du processus problématique et de l’examiner sans avoir à arrêter l’application.

## <a name="collect-dumps"></a>Collecter les vidages

Les vidages peuvent être collectés de différentes manières, en fonction de la plateforme sur laquelle vous exécutez votre application.

> [!NOTE]
> La collecte d’un vidage à l’intérieur d’un conteneur nécessite une fonctionnalité PTRACE, qui peut être ajoutée via `--cap-add=SYS_PTRACE` ou `--privileged` .

> [!NOTE]
> Les dumps peuvent contenir des informations sensibles, car elles peuvent contenir la mémoire complète du processus en cours d’exécution. Gérez-les avec des restrictions de sécurité et des recommandations à l’esprit.

### <a name="collecting-dumps-on-crash"></a>Collecte des vidages sur incident

Vous pouvez utiliser des variables d’environnement pour configurer votre application afin de collecter un vidage en cas d’incident. Cela est utile lorsque vous souhaitez comprendre pourquoi un incident s’est produit. Par exemple, la capture d’un vidage lorsqu’une exception est levée vous aide à identifier un problème en examinant l’état de l’application lorsqu’elle s’est bloquée.

Le tableau suivant répertorie les variables d’environnement que vous pouvez configurer pour collecter des vidages sur un incident.

|Variable d’environnement|Description|Valeur par défaut|
|-------|---------|---|
|`COMPlus_DbgEnableMiniDump`|Si la valeur est 1, active la génération de l’image mémoire principale.|0|
|`COMPlus_DbgMiniDumpType`|Type de vidage à collecter. Pour plus d’informations, consultez le tableau ci-dessous.|2 ( `MiniDumpWithPrivateReadWriteMemory` )|
|`COMPlus_DbgMiniDumpName`|Chemin d’accès à un fichier dans lequel écrire le vidage.|`/tmp/coredump.<pid>`|
|`COMPlus_CreateDumpDiagnostics`|Si la valeur est 1, active la journalisation des diagnostics du processus de vidage.|0|

Le tableau ci-dessous présente toutes les options que vous `COMPlus_DbgMiniDumpType` pouvez utiliser pour qui peuvent être spécifiées en tant que valeur. Par exemple, `COMPlus_DbgMiniDumpType` la valeur 1 signifie que `MiniDumpNormal` le type dump est collecté en cas d’incident.

|Valeur|Nom|Description|
|-----|----|-----------|
|1|`MiniDumpNormal`|Incluez uniquement les informations nécessaires pour capturer les traces de la pile pour tous les threads existants dans un processus. Mémoire et informations de tas GC limitées.|
|2|`MiniDumpWithPrivateReadWriteMemory`|Comprend les tas GC et les informations nécessaires à la capture des traces de la pile pour tous les threads existants dans un processus.|
|3|`MiniDumpFilterTriage`|Incluez uniquement les informations nécessaires pour capturer les traces de la pile pour tous les threads existants dans un processus. Mémoire et informations de tas GC limitées.|
|4|`MiniDumpWithFullMemory`|Incluez toute la mémoire accessible dans le processus. Les données de mémoire brutes sont incluses à la fin, afin que les structures initiales puissent être mappées directement sans les informations de mémoire brutes. Cette option peut aboutir à un fichier très volumineux.|

### <a name="collecting-dumps-at-specific-point-in-time"></a>Collecte des vidages à un moment précis dans le temps

Vous souhaiterez peut-être collecter un vidage lorsque l’application ne s’est pas encore bloquée. Par exemple, si vous souhaitez examiner l’état d’une application qui semble se trouver dans un blocage, la configuration des variables d’environnement pour collecter des vidages en cas d’incident n’est pas utile, car l’application est toujours en cours d’exécution.

Pour collecter un dump à votre propre demande, vous pouvez utiliser `dotnet-dump` , qui est un outil CLI pour la collecte et l’analyse des vidages. Pour plus d’informations sur la façon de les utiliser pour collecter des vidages avec `dotnet-dump` , consultez [dump collection and Analysis Utility](dotnet-dump.md).

## <a name="analyze-dumps"></a>Analyser les vidages

Vous pouvez anlayze des dumps à l’aide de l' [`dotnet-dump`](dotnet-dump.md) outil CLI ou de [Visual Studio](https://docs.microsoft.com/visualstudio/debugger/using-dump-files).

> [!NOTE]
> Visual Studio version 16,8 et versions ultérieures vous permet d' [ouvrir des vidages Linux](https://devblogs.microsoft.com/visualstudio/linux-managed-memory-dump-debugging/) générés sur .net Core 3.1.7 ou version ultérieure.  

> [!NOTE]
> Si le débogage natif est nécessaire, l' [extension de débogueur SOS](sos-debugging-extension.md) peut être utilisée avec [LLDB sur Linux et MacOS](debug-linux-dumps.md#analyze-dumps-on-linux). SOS est également pris en charge avec [WinDbg/CDB](/windows-hardware/drivers/debugger/debugger-download-tools) sur Windows, bien que Visual Studio soit recommandé.

## <a name="see-also"></a>Voir aussi

En savoir plus sur la façon dont vous pouvez tirer parti des vidages pour faciliter le diagnostic des problèmes dans votre application .NET.

* Le didacticiel sur le [débogage des vidages Linux](debug-linux-dumps.md) vous guide tout au long du débogage d’un vidage qui a été collecté dans Linux.

* Le didacticiel sur le [blocage du débogage](debug-deadlock.md) vous guide tout au long du débogage d’un interblocage dans votre application .net à l’aide de dumps.
