---
title: 'Modification avec rupture : CA2247 : l’argument du constructeur TaskCompletionSource doit être une valeur TaskCreationOptions'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code CA2247.
ms.date: 09/03/2020
ms.openlocfilehash: 323fd5a05da4dfeb68ef75d88d5d293ba01c8ade
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761033"
---
# <a name="warning-ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a>AVERTISSEMENT CA2247 : l’argument du constructeur TaskCompletionSource doit être une valeur TaskCreationOptions

La règle de l’analyseur de code .NET [CA2247](/visualstudio/code-quality/ca2247) est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour les appels au <xref:System.Threading.Tasks.TaskCompletionSource%601> constructeur qui passent un argument de type <xref:System.Threading.Tasks.TaskContinuationOptions> .

## <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md). Plusieurs de ces règles sont activées, par défaut, y compris [CA2247](/visualstudio/code-quality/ca2247). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

La règle CA2247 recherche les appels au <xref:System.Threading.Tasks.TaskCompletionSource%601> constructeur qui passent un argument de type <xref:System.Threading.Tasks.TaskContinuationOptions> . Le <xref:System.Threading.Tasks.TaskCompletionSource%601> type a un constructeur qui accepte une <xref:System.Threading.Tasks.TaskCreationOptions> valeur, et un autre constructeur qui accepte un <xref:System.Object> . Si vous transmettez une <xref:System.Threading.Tasks.TaskContinuationOptions> valeur par inadvertance au lieu d’une <xref:System.Threading.Tasks.TaskCreationOptions> valeur, le constructeur avec le <xref:System.Object> paramètre est appelé au moment de l’exécution. Votre code sera compilé et exécuté, mais n’aura pas le comportement prévu.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

- Remplacez l' <xref:System.Threading.Tasks.TaskContinuationOptions> argument par la <xref:System.Threading.Tasks.TaskCreationOptions> valeur correspondante. Ne supprimez pas cet avertissement, car il met presque toujours en évidence un bogue dans votre code. Pour plus d’informations, consultez [CA2247](/visualstudio/code-quality/ca2247).

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>API affectées

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

### Category

Code analysis

-->
