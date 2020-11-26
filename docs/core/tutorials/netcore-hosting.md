---
title: Écrire un hôte de runtime .NET Core personnalisé
description: Découvrez comment héberger le runtime .NET Core à partir du code natif pour prendre en charge des scénarios avancés nécessitant un contrôle du fonctionnement du runtime .NET Core.
author: mjrousos
ms.topic: how-to
ms.date: 12/21/2018
ms.openlocfilehash: 79336396de3058e40cf7328e6d92e7e9e54296e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242914"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Écrire un hôte .NET Core personnalisé pour contrôler le runtime .NET à partir de votre code natif

Comme tout code managé, les applications .NET Core sont exécutées par un hôte. L’hôte est chargé du démarrage du runtime (notamment des composants comme le JIT et le récupérateur de mémoire) et de l’appel des points d’entrée managés.

L’hébergement du runtime .NET Core est un scénario avancé et, dans la plupart des cas, les développeurs .NET Core n’ont pas à se soucier de l’hébergement, car les processus de génération .NET Core fournissent un hôte par défaut pour exécuter les applications .NET Core. Toutefois, dans certains cas spécifiques, il peut être utile d’héberger explicitement le runtime .NET Core, pour appeler le code managé dans un processus natif ou pour mieux contrôler le fonctionnement du runtime.

Cet article donne une vue d’ensemble des étapes nécessaires pour démarrer le runtime .NET Core à partir du code natif et y exécuter du code managé.

## <a name="prerequisites"></a>Prérequis

Étant donné que les hôtes sont des applications natives, ce didacticiel traite de la construction d’une application C++ pour héberger .NET Core. Vous avez besoin d’un environnement de développement C++ (comme celui fourni par [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Vous avez également besoin d’une application .NET Core simple pour tester l’hôte, vous devez donc installer le [SDK .NET Core](https://dotnet.microsoft.com/download) et [créer une petite application de test .NET Core](with-visual-studio.md) (par exemple, une application « Hello World »). L’application « Hello World » créée par le nouveau modèle de projet de console .NET Core est suffisante.

## <a name="hosting-apis"></a>API d’hébergement

Vous pouvez utiliser deux API différentes pour héberger .NET Core. Cet article (et ses [exemples](https://github.com/dotnet/samples/tree/master/core/hosting)associés) couvre ces deux options.

* La méthode d’hébergement conseillée pour le runtime .NET Core dans .NET Core 3.0 et versions ultérieures est d’utiliser les API des bibliothèques `nethost` et `hostfxr`. Ces points d’entrée gèrent la complexité de la recherche et de la configuration du runtime pour l’initialisation, et permettent à la fois de lancer une application managée et d’appeler une méthode managée statique.
* La méthode recommandée pour héberger le Runtime .NET Core avant .NET Core 3,0 est l' [`coreclrhost.h`](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API. Cette API expose des fonctions qui permettent de démarrer et d’arrêter facilement le runtime et d’appeler du code managé (soit en lançant un exécutable managé, soit en appelant des méthodes managées statiques).

## <a name="sample-hosts"></a>Exemples d’hôtes

Des [exemples d’hôtes](https://github.com/dotnet/samples/tree/master/core/hosting) illustrant les étapes décrites dans les tutoriels ci-dessous sont disponibles dans le dépôt GitHub dotnet/samples. Les commentaires dans les exemples associent clairement les étapes numérotées de ces tutoriels à l’endroit où elles sont exécutées dans l’exemple. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#view-and-download-samples).

N’oubliez pas que les exemples d’hôtes sont destinés à être utilisés dans un contexte d’apprentissage. Ils ne s’attardent donc pas sur la vérification des erreurs et privilégient la lisibilité par rapport à l’efficacité.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>Créer un hôte à l’aide `nethost.h` de et `hostfxr.h`

Les étapes suivantes décrivent comment utiliser les bibliothèques `nethost` et `hostfxr` pour démarrer le runtime .NET Core dans une application native et appeler une méthode statique managée. L' [exemple](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) utilise l' `nethost` en-tête et la bibliothèque installés avec le kit de développement logiciel (SDK) .net et des copies des [`coreclr_delegates.h`](https://github.com/dotnet/runtime/blob/master/src/installer/corehost/cli/coreclr_delegates.h) fichiers et du [`hostfxr.h`](https://github.com/dotnet/runtime/blob/master/src/installer/corehost/cli/hostfxr.h) référentiel [dotnet/Runtime](https://github.com/dotnet/runtime) .

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Étape 1 : charger `hostfxr` et obtenir les fonctions d’hébergement exportées

La bibliothèque `nethost` fournit la fonction `get_hostfxr_path` pour localiser la bibliothèque `hostfxr`. La bibliothèque `hostfxr` expose des fonctions pour l’hébergement du runtime .NET Core. Vous trouverez la liste complète des fonctions dans [`hostfxr.h`](https://github.com/dotnet/runtime/blob/master/src/installer/corehost/cli/hostfxr.h) et dans le [document de conception de l’hébergement natif](https://github.com/dotnet/runtime/blob/master/docs/design/features/native-hosting.md). L’exemple et ce didacticiel utilisent les éléments suivants :

* `hostfxr_initialize_for_runtime_config`: Initialise un contexte hôte et prépare l’initialisation du Runtime .NET Core à l’aide de la configuration du runtime spécifiée.
* `hostfxr_get_runtime_delegate`: Obtient un délégué pour les fonctionnalités d’exécution.
* `hostfxr_close`: Ferme un contexte hôte.

La bibliothèque `hostfxr` peut être obtenue avec `get_hostfxr_path`. Elle est ensuite chargée, et ses exportations sont récupérées.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Étape 2 : Initialiser et démarrer le runtime .NET Core

Les fonctions `hostfxr_initialize_for_runtime_config` et `hostfxr_get_runtime_delegate` initialisent et démarrent le runtime .NET Core à l’aide de la configuration du runtime pour le composant managé qui est chargé. La fonction `hostfxr_get_runtime_delegate` est utilisée pour obtenir un délégué de runtime qui permet le chargement d’un assembly managé et l’obtention d’un pointeur de fonction dans une méthode statique de cet assembly.

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Étape 3 : Charger l’assembly managé et obtenir le pointeur de fonction sur une méthode managée

Le délégué de runtime est appelé pour charger l’assembly managé et obtenir un pointeur de fonction vers une méthode managée. Le délégué nécessite le chemin d’accès de l’assembly, le nom de type et le nom de méthode en entrée, et retourne un pointeur de fonction qui peut être utilisé pour appeler la méthode managée.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

En passant `nullptr` comme nom de type de délégué lors de l’appel du délégué du runtime, l’exemple utilise une signature par défaut pour la méthode managée :

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Une signature différente peut être utilisée en spécifiant le nom du type de délégué lors de l’appel du délégué de runtime.

### <a name="step-4---run-managed-code"></a>Étape 4 : Exécuter le code managé !

L’hôte natif peut maintenant appeler la méthode managée et lui passer les paramètres souhaités.

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>Créer un hôte à l’aide de `coreclrhost.h`

Les étapes suivantes détaillent comment utiliser l' `coreclrhost.h` API pour démarrer le Runtime .net core dans une application native et appeler une méthode statique managée. Les extraits de code de ce document utilisent des API spécifiques à Windows, mais l’[exemple d’hôte complet](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) indique les chemins de code pour Windows et Linux.

L' [hôte de coexécution UNIX](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun) présente un exemple plus complexe et réaliste d’hébergement à l’aide de `coreclrhost.h` .

### <a name="step-1---find-and-load-coreclr"></a>Étape 1 : Rechercher et charger CoreCLR

Les API de runtime .NET Core se trouvent dans *coreclr.dll* (sur Windows), dans *libcoreclr.so* (sur Linux) ou dans *libcoreclr.dylib* (sur macOS). La première étape à suivre pour héberger .NET Core consiste à charger la bibliothèque CoreCLR. Certains hôtes sondent des chemins différents ou utilisent des paramètres d’entrée pour trouver la bibliothèque, tandis que d’autres savent la charger à partir d’un chemin donné (à côté de l’hôte, par exemple, ou à partir d’un emplacement dans l’ordinateur).

Une fois trouvé, la bibliothèque est chargée avec `LoadLibraryEx` (sur Windows) ou `dlopen` (sur Linux/MacOS).

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Étape 2 : Obtenir les fonctions d’hébergement .NET Core

CoreClrHost propose plusieurs méthodes importantes et utiles pour héberger .NET Core :

* `coreclr_initialize`: Démarre le Runtime .NET Core et configure l’AppDomain par défaut (et uniquement).
* `coreclr_execute_assembly`: Exécute un assembly managé.
* `coreclr_create_delegate`: Crée un pointeur de fonction vers une méthode managée.
* `coreclr_shutdown`: Arrête le Runtime .NET Core.
* `coreclr_shutdown_2`: Comme `coreclr_shutdown` , mais récupère également le code de sortie du code managé.

Après le chargement de la bibliothèque CoreCLR, l’étape suivante consiste à obtenir des références à ces fonctions à l’aide de `GetProcAddress` (sur Windows) ou `dlsym` (sur Linux/MacOS).

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Étape 3 : Préparer les propriétés du runtime

Avant de démarrer le runtime, il est nécessaire de préparer certaines propriétés pour spécifier le comportement (en particulier celui du chargeur d’assembly).

Parmi les propriétés communes, citons les suivantes :

* `TRUSTED_PLATFORM_ASSEMBLIES` Liste de chemins d’assembly (délimités par « ; » sur Windows et « : » sur Linux) que le runtime pourra résoudre par défaut. Certains hôtes ont des manifestes codés en dur listant les assemblys qu’ils peuvent charger. D’autres placent les bibliothèques à certains emplacements (par exemple, à côté de *coreclr.dll*) dans cette liste.
* `APP_PATHS` Il s’agit d’une liste de chemins où rechercher un assembly s’il est introuvable dans la liste TPA (liste d’assemblys de plateforme sécurisée). Étant donné que l’hôte a davantage de contrôle sur les assemblys chargés à l’aide de la liste TPA, il est recommandé aux hôtes de déterminer les assemblys qu’ils comptent charger et de les lister explicitement. Toutefois, si la détection au moment de l’exécution est nécessaire, cette propriété peut activer ce scénario.
* `APP_NI_PATHS` Cette liste est similaire à APP_PATHS, sauf qu’il s’agit de chemins où sonder des images natives.
* `NATIVE_DLL_SEARCH_DIRECTORIES` Cette propriété est une liste de chemins où le chargeur doit sonder les bibliothèques natives appelées avec p/invoke.
* `PLATFORM_RESOURCE_ROOTS` Cette liste comprend les chemins d’accès pour détecter les assemblys satellites de ressources (dans les sous-répertoires spécifiques à la culture).

Dans cet exemple d’hôte, la liste TPA est construite en listant simplement toutes les bibliothèques du répertoire actif :

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Comme l’exemple est simple, il n’a besoin que de la propriété `TRUSTED_PLATFORM_ASSEMBLIES` :

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Étape 4 : Démarrer le runtime

`coreclrhost.h` Les API démarrent le runtime et créent l’AppDomain par défaut tout avec un seul appel. La fonction `coreclr_initialize` prend un chemin de base, un nom et les propriétés décrites précédemment, puis retourne un descripteur à l’hôte par le biais du paramètre `hostHandle`.

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Étape 5 : Exécuter le code managé

Le runtime étant démarré, l’hôte peut appeler le code managé. Pour cela, deux méthodes sont disponibles. L’exemple de code lié à ce tutoriel utilise la fonction `coreclr_create_delegate` permettant de créer un délégué à une méthode managée statique. Cette API prend le [nom d’assembly](../../standard/assembly/names.md), le nom de type qualifié par un espace de noms et le nom de méthode comme entrées, puis retourne un délégué qui peut être utilisé pour appeler la méthode.

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

Dans cet exemple, l’hôte peut désormais appeler `managedDelegate` pour exécuter la méthode `ManagedWorker.DoWork`.

Vous pouvez également utiliser la fonction `coreclr_execute_assembly` pour lancer un exécutable managé. Cette API prend un chemin d’assembly et un tableau d’arguments comme paramètres d’entrée. Elle charge l’assembly à ce chemin et appelle sa méthode main.

```c++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Étape 6 : Arrêter et nettoyer

Enfin, quand l’hôte termine l’exécution du code managé, le runtime .NET Core est arrêté avec `coreclr_shutdown` ou `coreclr_shutdown_2`.

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR ne prend pas en charge la réinitialisation ou le déchargement. N’appelez pas `coreclr_initialize` à nouveau ou ne déchargez pas la bibliothèque CoreCLR.

## <a name="conclusion"></a>Conclusion

Une fois que votre hôte est créé, il peut être testé en l’exécutant à partir de la ligne de commande et en passant tous les arguments attendus par l’hôte. Quand vous spécifiez l’application .NET Core que l’hôte doit exécuter, utilisez le fichier .dll généré par `dotnet build`. Les exécutables (fichiers .exe) générés par `dotnet publish` pour les applications autonomes sont l’hôte .NET Core par défaut (pour que l’application puisse être lancée directement à partir de la ligne de commande dans les scénarios principaux) ; le code utilisateur est compilé dans une dll du même nom.

Si ce n’est pas le cas, double-Vérifiez que *coreclr.dll* est disponible à l’emplacement attendu par l’hôte, que toutes les bibliothèques d’infrastructure nécessaires se trouvent dans la liste TPA et que le nombre de bits de CoreCLR (32 bits ou 64 bits) correspond à la façon dont l’hôte a été créé.

L’hébergement du runtime .NET Core est un scénario avancé sans utilité pour un grand nombre de développeurs, mais qui peut être très utile pour ceux qui doivent lancer du code managé à partir d’un processus natif ou qui ont besoin de davantage de contrôle sur le comportement du runtime .NET Core.
