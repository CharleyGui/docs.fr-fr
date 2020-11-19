---
title: Collecter les diagnostics dans les conteneurs
description: Dans cet article, vous allez découvrir comment utiliser les outils de diagnostic de .NET Core dans les conteneurs de l’ancrage.
ms.date: 09/01/2020
ms.openlocfilehash: cf4bbdf75e943f093a2202f91303a2eea7125487
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916207"
---
# <a name="collect-diagnostics-in-containers"></a>Collecter les diagnostics dans les conteneurs

Les mêmes outils de diagnostic qui sont utiles pour diagnostiquer les problèmes de .NET Core dans d’autres scénarios fonctionnent également dans les conteneurs de l’ancrage. Toutefois, certains des outils requièrent des étapes spéciales pour travailler dans un conteneur. Cet article explique comment utiliser les outils pour rassembler des traces de performances et collecter des vidages dans des conteneurs dockers.

## <a name="using-net-core-cli-tools-in-a-container"></a>Utilisation d’outils de CLI .NET Core dans un conteneur

**Ces outils s’appliquent à : ✔️ Kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

Les outils de diagnostic globaux de l’interface CLI .net Core ( [`dotnet-counters`](dotnet-counters.md) , [`dotnet-dump`](dotnet-dump.md) , [`dotnet-gcdump`](dotnet-gcdump.md) et [`dotnet-trace`](dotnet-trace.md) ) sont conçus pour fonctionner dans un large éventail d’environnements et doivent tous fonctionner directement dans les conteneurs de l’ancrage. Pour cette raison, ces outils sont la méthode recommandée pour collecter des informations de diagnostic pour les scénarios .NET Core ciblant .NET Core 3,0 ou une version ultérieure (ou 3,1 ou version ultérieure dans le cas de `dotnet-gcdump` ) dans des conteneurs.

Le seul facteur de compliquation de l’utilisation de ces outils dans un conteneur est qu’ils sont installés avec le kit SDK .NET Core et que de nombreux conteneurs de l’arrimeur s’exécutent sans l’kit SDK .NET Core présent. Une solution simple à ce problème consiste à installer les outils dans l’image initiale de l’ancrage. Les outils n’ont pas besoin de l’kit SDK .NET Core pour être exécutés, mais uniquement pour être installés. Par conséquent, il est possible de créer un fichier dockerfile avec une [Build à plusieurs étapes](https://docs.docker.com/develop/develop-images/multistage-build/) qui installe les outils dans une étape de génération (où le kit SDK .net Core est présent), puis copie les fichiers binaires dans l’image finale. Le seul inconvénient de cette approche est l’augmentation de la taille de l’image de l’ancrage.

```dockerfile
# In build stage
# Install desired .NET CLI diagnostics tools
RUN dotnet tool install --tool-path /tools dotnet-trace
RUN dotnet tool install --tool-path /tools dotnet-counters
RUN dotnet tool install --tool-path /tools dotnet-dump

...

# In final stage
# Copy diagnostics tools
WORKDIR /tools
COPY --from=build /tools .
```

Vous pouvez également installer le kit SDK .NET Core dans un conteneur si nécessaire pour installer les outils CLI. N’oubliez pas que l’installation du kit SDK .NET Core aura l’effet secondaire de réinstaller le Runtime .NET Core. Veillez donc à installer la version du kit de développement logiciel (SDK) qui correspond au runtime présent dans le conteneur.

### <a name="using-net-core-global-cli-tools-in-a-sidecar-container"></a>Utilisation des outils CLI globaux .NET Core dans un conteneur side-car

Si vous souhaitez utiliser les outils de diagnostic de l’interface CLI .NET Core globaux pour diagnostiquer les processus dans un autre conteneur, vous devez tenir compte des conditions supplémentaires suivantes :

1. Les conteneurs doivent [partager un espace de noms de processus](https://docs.docker.com/engine/reference/run/#pid-settings---pid) (afin que les outils dans le conteneur side-car puissent accéder aux processus dans le conteneur cible).
2. Les outils de diagnostic de l’interface CLI .NET Core doivent accéder aux fichiers que le Runtime .NET Core écrit dans le répertoire/tmp, de sorte que le répertoire/tmp doit être partagé entre le conteneur cible et le conteneur side-car via un montage de volume. Cela peut être fait, par exemple, en faisant en sorte que les conteneurs partagent un [volume commun ou un volume Kubernetes](https://docs.docker.com/storage/volumes/#create-and-manage-volumes) [emptyDir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) . Si vous tentez d’utiliser les outils de diagnostic à partir d’un conteneur side-car sans partager le répertoire/tmp, vous obtiendrez une erreur concernant le processus « pas en cours d’exécution du Runtime .NET compatible ».

## <a name="using-perfcollect-in-a-container"></a>Utilisation `PerfCollect` dans un conteneur

**Cet outil s’applique à : ✔️** .net Core 2,1 et versions ultérieures

Le [`PerfCollect`](./trace-perfcollect-lttng.md) script est utile pour la collecte des traces de performances et est l’outil recommandé pour la collecte des traces avant .net Core 3,0. Si vous utilisez `PerfCollect` dans un conteneur, gardez à l’esprit les exigences suivantes :

1. `PerfCollect`nécessite la [ `SYS_ADMIN` fonctionnalité](https://man7.org/linux/man-pages/man7/capabilities.7.html) (pour exécuter l' `perf` outil), assurez-vous que le conteneur est [démarré avec cette fonctionnalité](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).
2. `PerfCollect` certaines variables d’environnement doivent être définies avant le profilage de l’application. Ils peuvent être définis dans un [fichier dockerfile](https://docs.docker.com/engine/reference/builder/#env) ou lors [du démarrage du conteneur](https://docs.docker.com/engine/reference/run/#env-environment-variables). Étant donné que ces variables ne doivent pas être définies dans des environnements de production normaux, il est courant de les ajouter simplement au démarrage d’un conteneur qui sera profilé. Les deux variables requises par PerfCollect sont les suivantes :
    1. COMPlus_PerfMapEnabled = 1
    1. COMPlus_EnableEventLog = 1

### <a name="using-perfcollect-in-a-sidecar-container"></a>Utilisation `PerfCollect` dans un conteneur side-car

Si vous souhaitez exécuter `PerfCollect` dans un conteneur pour profiler un processus .net core dans un autre conteneur, l’expérience est presque la même, à l’exception de ces différences :

1. Les variables d’environnement mentionnées précédemment (COMPlus_PerfMapEnabled et COMPlus_EnableEventLog) doivent être définies pour le conteneur cible (pas celle en cours d’exécution `PerfCollect` ).
2. Le conteneur en cours d’exécution `PerfCollect` doit avoir la `SYS_ADMIN` capacité (et non le conteneur cible).
3. Les deux conteneurs doivent [partager un espace de noms de processus](https://docs.docker.com/engine/reference/run/#pid-settings---pid).

## <a name="using-createdump-in-a-container"></a>Utilisation `createdump` dans un conteneur

**Cet outil s’applique à : ✔️** .net Core 2,1 et versions ultérieures

Une alternative à `dotnet-dump` , [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) peut être utilisée pour créer des vidages principaux sur Linux contenant des informations natives et gérées. L' `createdump` outil est installé avec le Runtime .net Core et se trouve en regard de libcoreclr.so (généralement dans « /usr/share/dotnet/Shared/Microsoft.NETCore.app/[version] »). L’outil fonctionne de la même manière dans un conteneur que dans les environnements Linux non conteneurs, à l’exception près que l’outil requiert la [ `SYS_PTRACE` fonctionnalité](https://man7.org/linux/man-pages/man7/capabilities.7.html), de sorte que le conteneur de la station d’accueil doit être [démarré avec cette fonctionnalité](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).

### <a name="using-createdump-in-a-sidecar-container"></a>Utilisation `createdump` dans un conteneur side-car

Si vous souhaitez utiliser `createdump` pour créer un vidage à partir d’un processus dans un autre conteneur, l’expérience est presque la même, à l’exception de ces différences :

1. Le conteneur en cours d’exécution `createdump` doit avoir la `SYS_PTRACE` capacité (et non le conteneur cible).
2. Les deux conteneurs doivent [partager un espace de noms de processus](https://docs.docker.com/engine/reference/run/#pid-settings---pid).
