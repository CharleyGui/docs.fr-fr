---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802446"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Génération de code incorrecte lors de la transmission et de la comparaison de valeurs UInt16

|   |   |
|---|---|
|Détails|En raison de modifications introduites dans .NET Framework 4.7, le code généré par le compilateur JIT dans les applications exécutées sur .NET Framework 4.7 compare parfois de façon incorrecte deux valeurs <code>T:System.UInt16</code>. Pour plus d’informations, consultez [Problème n°11508 : Codegen incorrect non signalé lors de la transmission et de la comparaison d’arguments ushort](https://github.com/dotnet/coreclr/issues/11508) sur GitHub.com.|
|Suggestion|Si vous rencontrez des problèmes lors de la comparaison de valeurs non signées 16 bits dans .NET Framework 4.7, effectuez la mise à niveau vers .NET Framework 4.7.1.|
|Étendue|Edge|
|Version|4,7|
|Type|Runtime|
