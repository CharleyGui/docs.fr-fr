---
ms.openlocfilehash: 4fc31f75e8f8cdd50abebd399d9749688e6faa5a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465572"
---
### <a name="ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a>CA2015 : Ne pas définir de finaliseurs pour les types dérivés de MemoryManager\<T>

La [règle de](/visualstudio/code-quality/ca2015) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour tous les types qui dérivent de <xref:System.Buffers.MemoryManager%601> qui définissent un finaliseur.

#### <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md). Plusieurs de ces règles sont activées par défaut, y compris [ca2015](/visualstudio/code-quality/ca2015). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

Règle ca2015 signale les types qui dérivent de <xref:System.Buffers.MemoryManager%601> qui définissent un finaliseur. L’ajout d’un finaliseur à un type qui dérive de <xref:System.Buffers.MemoryManager%601> est probablement une indication d’un bogue. Elle suggère qu’une ressource native qui aurait pu être obtenue dans un est en cours de <xref:System.Span%601> nettoyage, éventuellement pendant qu’elle est toujours utilisée par le <xref:System.Span%601> .

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

- Supprimez la définition du finaliseur. Pour plus d’informations, consultez [ca2015](/visualstudio/code-quality/ca2015).

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Category

Analyse du code

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
