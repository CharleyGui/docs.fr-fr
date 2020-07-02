---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615676"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>Instruction IL ret non autorisée dans une zone try

#### <a name="details"></a>Détails

À la différence du compilateur juste-à-temps JIT 64 bits, RyuJIT (utilisé dans .NET Framework 4.6) n’autorise pas une instruction IL ret dans une zone try. Le retour à partir d’une zone try n’est pas autorisé par la spécification ECMA-335. Par ailleurs, aucun compilateur managé connu ne génère ce type de code IL. Toutefois, le compilateur JIT64 exécute ce code IL, s'il est généré à l'aide de l'émission de réflexion.

#### <a name="suggestion"></a>Suggestion

Si une application génère du code IL qui inclut un opcode ret dans une zone try, l’application peut cibler .NET Framework 4.5 pour utiliser l’ancien JIT et éviter cette interruption de l’exécution. Il est également possible de mettre à jour le code IL généré pour qu’il soit retourné après la zone try.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6         |
| Type    | Reciblage |
