---
title: Collecter des informations détaillées sur le chargement de l’assembly-.NET Core
description: Description de la collecte des informations de chargement d’assembly dans .NET Core
author: elinor-fung
ms.author: elfung
ms.date: 11/17/2020
ms.openlocfilehash: b121982995b440ade6d72190f44f9b9d237c8af6
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506584"
---
# <a name="collect-detailed-assembly-loading-information"></a>Collecter des informations détaillées sur le chargement d’assembly

À compter de .NET 5,0, le runtime peut émettre `EventPipe` des événements avec des informations détaillées sur le [chargement d’assemblys managés](loading-managed.md) pour faciliter le diagnostic des problèmes de chargement d’assembly. Ces [événements](../../fundamentals/diagnostics/runtime-loader-binder-events.md) sont émis par le `Microsoft-Windows-DotNETRuntime` fournisseur sous le `AssemblyLoader` mot clé ( `0x4` ).

## <a name="prerequisites"></a>Prérequis

- [.Net 5,0 SDK](https://dotnet.microsoft.com/download) ou versions ultérieures
- outil [dotnet-trace](../diagnostics/dotnet-trace.md) .

## <a name="collect-a-trace-with-assembly-loading-events"></a>Collecter une trace avec des événements de chargement d’assembly

Pour activer les événements de chargement d’assembly dans le runtime et en collecter une trace, utilisez `dotnet-trace` avec la commande suivante :

```console
dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id <pid>
```

Cela permet de collecter une trace du spécifié `<pid>` , en activant les `AssemblyLoader` événements dans le `Microsoft-Windows-DotNETRuntime` fournisseur. Le résultat est un `.nettrace` fichier.

## <a name="view-a-trace"></a>Afficher une trace

Le fichier de trace collecté peut être affiché sur Windows à l’aide de la vue événements dans [PerfView](https://github.com/microsoft/perfview). Tous les événements de chargement d’assembly seront précédés de `Microsoft-Windows-DotNETRuntime/AssemblyLoader` .

## <a name="example-on-windows"></a>Exemple (sur Windows)

Cet exemple utilise l' [exemple de points d’extension de chargement d’assembly](https://github.com/dotnet/samples/tree/master/core/extensions/AssemblyLoading). L’application tente de charger un assembly `MyLibrary` : il s’agit d’un assembly qui n’est pas référencé par l’application et qui, par conséquent, doit être géré dans un point d’extension de chargement d’assembly pour être correctement chargé.

### <a name="collect-the-trace"></a>Collecter la trace

01. Accédez au répertoire à l’aide de l’exemple téléchargé. Générez l’application avec :

    ```console
    dotnet build
    ```

01. Lancez l’application avec des arguments indiquant qu’elle doit s’interrompre, en attendant une pression sur une touche. Lors de la reprise, il tente de charger l’assembly dans la valeur par défaut, `AssemblyLoadContext` sans la gestion nécessaire pour un chargement réussi. Accédez au répertoire de sortie et exécutez :

    ```console
    AssemblyLoading.exe /d default
    ```

01. Recherchez l’ID de processus de l’application.

    ```console
    dotnet-trace ps
    ```

    La sortie répertorie les processus disponibles. Par exemple :

    ```console
    35832 AssemblyLoading C:\src\AssemblyLoading\bin\Debug\net5.0\AssemblyLoading.exe
    ```

01. Attachement `dotnet-trace` à l’application en cours d’exécution.

    ```console
    dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id 35832
    ```

01. Dans la fenêtre qui exécute l’application, appuyez sur n’importe quelle touche pour permettre au programme de continuer. Le suivi s’arrêtera automatiquement une fois l’application fermée.

### <a name="view-the-trace"></a>Afficher la trace

Ouvrez la trace collectée dans [PerfView](https://github.com/microsoft/perfview) et ouvrez la vue événements. Filtrer la liste des événements sur `Microsoft-Windows-DotNETRuntime/AssemblyLoader` événements.

:::image type="content" source="media/collect-details/assembly-loader-filter.png" alt-text="Image de filtre de chargeur d’assembly PerfView":::

Tous les chargements d’assembly qui se sont produits dans l’application après le démarrage du suivi s’affichent. Pour inspecter l’opération de chargement de l’assembly d’intérêt pour cet exemple `MyLibrary` , nous pouvons effectuer d’autres opérations de filtrage.

### <a name="assembly-loads"></a>Chargements d’assemblys

Filtrez l’affichage avec [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) les [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) événements et sous `Microsoft-Windows-DotNETRuntime/AssemblyLoader` à l’aide de la liste d’événements sur la gauche. Ajoutez les colonnes `AssemblyName` , `ActivityID` et `Success` à la vue. Filtrez les événements contenant `MyLibrary` .

:::image type="content" source="media/collect-details/start-stop.png" alt-text="Image des événements de démarrage et d’arrêt PerfView":::

| Nom de l'événement             | AssemblyName                                      | ActivityID | Succès |
| ---------------------- | ------------------------------------------------- | ---------- | ------- |
| `AssemblyLoader/Start` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | 1/2/     |         |
| `AssemblyLoader/Stop`  | `MyLibrary, Culture=neutral, PublicKeyToken=null` | 1/2/     | False   |

Vous devez voir une `Start` / `Stop` paire avec `Success=False` sur l' `Stop` événement, indiquant que l’opération de chargement a échoué. Notez que les deux événements ont le même ID d’activité. L’ID d’activité peut être utilisé pour filtrer tous les autres événements d’assembly Loader sur ceux correspondant à cette opération de chargement.

### <a name="breakdown-of-attempt-to-load"></a>Répartition de la tentative de chargement

Pour une répartition plus détaillée de l’opération de chargement, filtrez la vue sur les [ `ResolutionAttempted` événements](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event) sous `Microsoft-Windows-DotNETRuntime/AssemblyLoader` à l’aide de la liste des événements sur la gauche. Ajoutez les colonnes `AssemblyName` , `Stage` et `Result` à la vue. Filtrez les événements avec l’ID d’activité de la `Start` / `Stop` paire.

:::image type="content" source="media/collect-details/resolution-attempted.png" alt-text="Image des événements PerfView ResolutionAttempted":::

| Nom de l'événement                           | AssemblyName                                      | Étape                               | Résultats             |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AppDomainAssemblyResolveEvent`     | `AssemblyNotFound` |

Les événements ci-dessus indiquent que le chargeur d’assembly a tenté de résoudre l’assembly en examinant le contexte de chargement actuel, en exécutant la logique de détection par défaut pour les assemblys d’application managée, en appelant des gestionnaires pour l' <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> événement et en appelant des gestionnaires pour le <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> . Pour toutes ces étapes, l’assembly est introuvable.

### <a name="extension-points"></a>Points d’extension

Pour connaître les points d’extension qui ont été appelés, filtrez la vue sur [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) et [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) sous `Microsoft-Windows-DotNETRuntime/AssemblyLoader` à l’aide de la liste des événements sur la gauche. Ajoutez les colonnes `AssemblyName` et `HandlerName` à la vue. Filtrez les événements avec l’ID d’activité de la `Start` / `Stop` paire.

:::image type="content" source="media/collect-details/extension-point.png" alt-text="Image des événements du point d’extension PerfView":::

| Nom de l'événement                                                  | AssemblyName                                      | HandlerName                      |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` |
| `AssemblyLoader/AppDomainAssemblyResolveHandlerInvoked`     | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAppDomainAssemblyResolve`     |

Les événements ci-dessus indiquent qu’un gestionnaire nommé `OnAssemblyLoadContextResolving` a été appelé pour l' <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> événement et qu’un gestionnaire nommé `OnAppDomainAssemblyResolve` était appelé pour l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.

### <a name="collect-another-trace"></a>Collecter une autre trace

Exécutez l’application avec des arguments de sorte que son gestionnaire de l' <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> événement charge l' `MyLibrary` assembly.

```console
AssemblyLoading /d default alc-resolving
```

Collectez et ouvrez un autre `.nettrace` fichier à l’aide [de la procédure décrite ci-dessus](#collect-the-trace).

Filtrez les `Start` `Stop` événements et de `MyLibrary` nouveau. Vous devez voir une `Start` / `Stop` paire avec une autre `Start` / `Stop` . L’opération de chargement interne représente la charge déclenchée par le gestionnaire <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> lors de son appel <xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType> . Cette fois, vous devez voir `Success=True` sur l' `Stop` événement, indiquant que l’opération de chargement a réussi. Le `ResultAssemblyPath` champ affiche le chemin d’accès de l’assembly résultant.

:::image type="content" source="media/collect-details/start-stop-success.png" alt-text="Image d’événements de démarrage et d’arrêt de PerfView réussie":::

| Nom de l'événement             | AssemblyName                                                       | ActivityID | Succès | ResultAssemblyPath                                      |
| ---------------------- | ------------------------------------------------------------------ |------------|---------| ------------------------------------------------------- |
| `AssemblyLoader/Start` |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | 1/2/     |         |                                                         |
| `AssemblyLoader/Start` | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | 1/2/1/   |         |                                                         |
| `AssemblyLoader/Stop`  | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | 1/2/1/   | True    | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |
| `AssemblyLoader/Stop`  |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | 1/2/     | True    | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

Nous pouvons ensuite examiner les `ResolutionAttempted` événements avec l’ID d’activité de la charge externe pour déterminer l’étape à laquelle l’assembly a été résolu avec succès. Cette fois-ci, les événements indiquent que l' `AssemblyLoadContextResolvingEvent` étape a réussi. Le `ResultAssemblyPath` champ affiche le chemin d’accès de l’assembly résultant.

:::image type="content" source="media/collect-details/resolution-attempted-success.png" alt-text="Image d’événements ResolutionAttempted réussie PerfView":::

| Nom de l'événement                           | AssemblyName                                      | Étape                               | Résultats             | ResultAssemblyPath |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `Success`          | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

L’examen `AssemblyLoadContextResolvingHandlerInvoked` des événements indique que le gestionnaire nommé `OnAssemblyLoadContextResolving` a été appelé. Le `ResultAssemblyPath` champ affiche le chemin d’accès de l’assembly retourné par le gestionnaire.

:::image type="content" source="media/collect-details/extension-point-success.png" alt-text="Image des événements du point d’extension PerfView réussie":::

| Nom de l'événement                                                  | AssemblyName                                      | HandlerName                      | ResultAssemblyPath |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- | ------------------ |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

Notez qu’il n’y a plus d' `ResolutionAttempted` événement avec l' `AppDomainAssemblyResolveEvent` étape ou les `AppDomainAssemblyResolveHandlerInvoked` événements, car l’assembly a été chargé avec succès avant d’atteindre l’étape de l’algorithme de chargement qui déclenche l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.

## <a name="see-also"></a>Voir aussi

- [Événements du chargeur d’assembly](../../fundamentals/diagnostics/runtime-loader-binder-events.md)
- [dotnet-trace](../diagnostics/dotnet-trace.md)
- [PerfView](https://github.com/microsoft/perfview)
