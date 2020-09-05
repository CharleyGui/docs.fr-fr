---
ms.openlocfilehash: 018c99d60dc8926cae2682dc9c035e25fba711e5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497806"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Génération de code incorrecte lors de la transmission et de la comparaison de valeurs UInt16

#### <a name="details"></a>Détails

En raison de modifications introduites dans .NET Framework 4.7, le code généré par le compilateur JIT dans les applications exécutées sur .NET Framework 4.7 compare parfois de façon incorrecte deux valeurs <code>T:System.UInt16</code>. Pour plus d’informations, consultez [Problème n°11508 : Codegen incorrect non signalé lors de la transmission et de la comparaison d’arguments ushort](https://github.com/dotnet/coreclr/issues/11508) sur GitHub.com.

#### <a name="suggestion"></a>Suggestion

Si vous rencontrez des problèmes lors de la comparaison de valeurs non signées 16 bits dans .NET Framework 4.7, effectuez la mise à niveau vers .NET Framework 4.7.1.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,7|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
