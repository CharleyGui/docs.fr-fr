---
ms.openlocfilehash: c20d5fb3d700ba7649e423a79e4598b327c50a00
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622239"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Génération de code incorrecte lors de la transmission et de la comparaison de valeurs UInt16

#### <a name="details"></a>Détails

En raison de modifications introduites dans .NET Framework 4.7, le code généré par le compilateur JIT dans les applications exécutées sur .NET Framework 4.7 compare parfois de façon incorrecte deux valeurs <code>T:System.UInt16</code>. Pour plus d’informations, consultez [Problème n°11508 : Codegen incorrect non signalé lors de la transmission et de la comparaison d’arguments ushort](https://github.com/dotnet/coreclr/issues/11508) sur GitHub.com.

#### <a name="suggestion"></a>Suggestion

Si vous rencontrez des problèmes lors de la comparaison de valeurs non signées 16 bits dans .NET Framework 4.7, effectuez la mise à niveau vers .NET Framework 4.7.1.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,7|
|Type|Runtime|
