---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804486"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>Instruction IL ret non autorisée dans une zone try

|   |   |
|---|---|
|Détails|À la différence du compilateur juste-à-temps JIT 64 bits, RyuJIT (utilisé dans .NET Framework 4.6) n’autorise pas une instruction IL ret dans une zone try. Le retour à partir d’une zone try n’est pas autorisé par la spécification ECMA-335. Par ailleurs, aucun compilateur managé connu ne génère ce type de code IL. Toutefois, le compilateur JIT64 exécute ce code IL, s'il est généré à l'aide de l'émission de réflexion.|
|Suggestion|Si une application génère du code IL qui inclut un opcode ret dans une zone try, l’application peut cibler .NET Framework 4.5 pour utiliser l’ancien JIT et éviter cette interruption de l’exécution. Il est également possible de mettre à jour le code IL généré pour qu’il soit retourné après la zone try.|
|Étendue|Edge|
|Version|4.6|
|Type|Reciblage|
