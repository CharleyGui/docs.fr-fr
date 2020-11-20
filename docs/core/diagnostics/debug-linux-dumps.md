---
title: Déboguer des vidages Linux
description: Dans cet article, vous allez apprendre à collecter et à analyser les vidages des environnements Linux.
ms.date: 08/27/2020
ms.openlocfilehash: 692d6228fae31de015412c23c4ec5317024faaab
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982260"
---
# <a name="debug-linux-dumps"></a>Déboguer des vidages Linux

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="collect-dumps-on-linux"></a>Collecter des vidages sur Linux

Les deux méthodes recommandées pour collecter des vidages sur Linux sont les [`dotnet-dump`](dotnet-dump.md) [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) outils ou.

### <a name="managed-dumps-with-dotnet-dump"></a>Dumps managés avec `dotnet-dump`

L' [`dotnet-dump`](dotnet-dump.md) outil est simple à utiliser et n’a pas de dépendance sur les débogueurs natifs. `dotnet-dump` fonctionne sur un large éventail de plates-formes Linux (telles que Alpine ou ARM32/ARM64) où les outils de débogage traditionnels ne sont peut-être pas disponibles. Toutefois, `dotnet-dump` ne capture que l’état managé afin qu’il ne puisse pas être utilisé pour déboguer des problèmes en code natif. Les vidages collectés par `dotnet-dump` sont analysés dans un environnement avec le système d’exploitation et l’architecture sur lesquels le dump a été créé. L' [`dotnet-gcdump`](dotnet-gcdump.md) outil peut être utilisé comme alternative qui capture uniquement les informations du tas GC, mais produit des vidages qui peuvent être analysés sur Windows.

### <a name="core-dumps-with-createdump"></a>Vidages principaux avec `createdump`

Une alternative à `dotnet-dump` qui crée des dumps managés uniquement, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) est l’outil recommandé pour créer des vidages principaux sur Linux contenant des informations natives et managées. D’autres outils tels que gdb ou gcore peuvent également être utilisés pour créer des vidages essentiels, mais ils peuvent manquer d’État pour le débogage managé, ce qui entraîne des noms de type ou de fonction « inconnus » lors de l’analyse.

Les `createdump` outils sont installés avec le Runtime .net Core et se trouvent en regard de libcoreclr.so (généralement dans « /usr/share/dotnet/Shared/Microsoft.NETCore.app/[version] »). L’outil prend un ID de processus pour collecter un dump à partir de comme son argument principal et peut également accepter des paramètres facultatifs qui spécifient le type de vidage à collecter (un minidump avec segment de mémoire est la valeur par défaut). Les options sont les suivantes :

- **`<input-filename>`**

  Fichier de trace d’entrée à convertir. La valeur par défaut est *trace. NetTrace*.

### <a name="options"></a>Options

- **`-f|--name <output-filename>`**

  Fichier dans lequel écrire le vidage. La valeur par défaut est « /tmp/coredump.%p », où% p est l’ID de processus du processus cible.

- **`-n|--normal`**

  Créez un minidump.

- **`-h|--withheap`**

  Créez un minidump avec segment mémoire (par défaut).

- **`-t|--triage`**

  Créez un minidump de triage.

- **`-u|--full`**

  Créez un vidage de noyau complet.

- **`-d|--diag`**

  Activez les messages de diagnostic.

Notez que la collecte des vidages centraux requiert la `SYS_PTRACE` fonctionnalité ou l' `createdump` exécution avec sudo ou su.

## <a name="analyze-dumps-on-linux"></a>Analyser les vidages sur Linux

Les dumps managés collectés avec `dotnet-dump` et les vidages de noyau collectés avec `createdump` peuvent être analysés avec l' `dotnet-dump` outil à l’aide de la `dotnet-dump analyze` commande. Le `dotnet dump` requiert que l’environnement qui analyse le dump ait le même système d’exploitation et l’même architecture que l’environnement dans lequel le dump a été capturé.

Vous pouvez également utiliser [LLDB](https://lldb.llvm.org/) pour analyser les vidages principaux sur Linux, ce qui permet l’analyse des frames managés et natifs. LLDB utilise l’extension SOS pour déboguer le code managé. L' [`dotnet-sos`](dotnet-sos.md) outil CLI peut être utilisé pour installer SOS, qui contient de [nombreuses commandes utiles](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) pour déboguer le code managé. Pour analyser les vidages .NET Core, LLDB et SOS requièrent les binaires .NET Core suivants de l’environnement dans lequel le dump a été créé :

1. libmscordaccore.so
2. libcoreclr.so
3. dotnet (l’hôte utilisé pour lancer l’application)

Dans la plupart des cas, ces fichiers binaires peuvent être téléchargés à l’aide de l' [`dotnet-symbol`](dotnet-symbol.md) outil. Si les fichiers binaires nécessaires ne peuvent pas être téléchargés avec `dotnet-symbol` (par exemple, si une version privée de .net Core générée à partir de la source était en cours d’utilisation), il peut être nécessaire de copier les fichiers listés ci-dessus à partir de l’environnement dans lequel le dump a été créé. Si les fichiers ne sont pas situés à côté du fichier dump, vous pouvez utiliser la commande LLDB/SOS `setclrpath <path>` pour définir le chemin à partir duquel ils doivent être chargés et `setsymbolserver -directory <path>` pour définir le chemin d’accès à rechercher pour les fichiers de symboles.

Une fois les fichiers nécessaires disponibles, le vidage peut être chargé dans LLDB en spécifiant l’hôte dotnet comme exécutable à déboguer :

```console
lldb --core <dump-file> <host-program>
```

Dans la ligne de commande ci-dessus, `<dump-file>` est le chemin d’accès de l’image mémoire à analyser et `<host-program>` est le programme natif qui a démarré l’application .net core. Il s’agit généralement du `dotnet` binaire, à moins que l’application ne soit autonome, auquel cas il s’agit du nom de l’application sans l’extension dll.

Une fois LLDB démarré, il peut être nécessaire d’utiliser la `setsymbolserver` commande pour pointer vers l’emplacement de symbole approprié ( `setsymbolserver -ms` pour utiliser le serveur de symboles de Microsoft ou `setsymbolserver -directory <path>` pour spécifier un chemin d’accès local). Les symboles natifs peuvent être chargés en exécutant `loadsymbols` . À ce stade, les [commandes SOS](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) peuvent être utilisées pour analyser le vidage.

## <a name="see-also"></a>Voir aussi

- [dotnet-SOS](dotnet-sos.md) pour plus d’informations sur l’installation de l’extension SOS.
- [dotnet-Symbol](dotnet-symbol.md) pour plus d’informations sur l’installation et l’utilisation de l’outil de téléchargement de symboles.
- [Diagnostics .net Core référentiel](https://github.com/dotnet/diagnostics/blob/master/documentation/) pour plus d’informations sur le débogage, y compris un Forum aux questions utile.
- [Installation de LLDB](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) pour obtenir des instructions sur l’installation de LLDB sur Linux ou Mac.
