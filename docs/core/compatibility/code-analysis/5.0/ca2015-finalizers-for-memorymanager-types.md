---
title: 'Modification avec rupture : ca2015 : ne définissez pas de finaliseurs pour les types dérivés de MemoryManager<T>'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca2015.
ms.date: 09/03/2020
ms.openlocfilehash: 5d0ba0546b5a72363559f23713c8af4bb4e26e48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760812"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a>AVERTISSEMENT ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager\<T>

La [règle de](/visualstudio/code-quality/ca2015) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour tous les types qui dérivent de <xref:System.Buffers.MemoryManager%601> qui définissent un finaliseur.

## <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md). Plusieurs de ces règles sont activées par défaut, y compris [ca2015](/visualstudio/code-quality/ca2015). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

Règle ca2015 signale les types qui dérivent de <xref:System.Buffers.MemoryManager%601> qui définissent un finaliseur. L’ajout d’un finaliseur à un type qui dérive de <xref:System.Buffers.MemoryManager%601> est probablement une indication d’un bogue. Elle suggère qu’une ressource native qui aurait pu être obtenue dans un est en cours de <xref:System.Span%601> nettoyage, éventuellement pendant qu’elle est toujours utilisée par le <xref:System.Span%601> .

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

- Supprimez la définition du finaliseur. Pour plus d’informations, consultez [ca2015](/visualstudio/code-quality/ca2015).

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
