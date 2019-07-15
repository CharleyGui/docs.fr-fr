---
ms.openlocfilehash: 060da3ebc60057554fd572bd2569652afee6bd0f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804486"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>Instruction IL ret non autorisée dans une zone try

|   |   |
|---|---|
|Détails|À la différence du compilateur juste-à-temps JIT 64 bits, RyuJIT (utilisé dans .NET Framework 4.6) n’autorise pas une instruction IL ret dans une zone try. Le retour à partir d’une zone try n’est pas autorisé par la spécification ECMA-335. Par ailleurs, aucun compilateur managé connu ne génère ce type de code IL. Toutefois, le compilateur JIT64 exécute ce code IL, s'il est généré à l'aide de l'émission de réflexion.|
|Suggestion|Si une application génère du code IL qui inclut un opcode ret dans une zone try, l’application peut cibler .NET Framework 4.5 pour utiliser l’ancien JIT et éviter cette interruption de l’exécution. Il est également possible de mettre à jour le code IL généré pour qu’il soit retourné après la zone try.|
|Portée|Microsoft Edge|
|Version|4.6|
|Type|Reciblage|

