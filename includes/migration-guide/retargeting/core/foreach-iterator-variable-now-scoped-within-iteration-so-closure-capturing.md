---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617203"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>La variable d’itérateur foreach est désormais délimitée au sein de l’itération. La sémantique de capture de clôture est donc différente (en C# 5)

#### <a name="details"></a>Détails

À compter de C# 5 (Visual Studio 2012), les variables d’itérateur `foreach` sont délimitées au sein de l’itération. Cela peut provoquer des arrêts d’exécution si le code dépendait du fait que les variables ne soient pas incluses dans la clôture de `foreach`. Les conséquences de ce changement sont qu’une variable d’itérateur passée à un délégué est considérée comme la valeur qu’elle a au moment où le délégué est créé, plutôt que comme la valeur qu’elle a au moment où le délégué est appelé.

#### <a name="suggestion"></a>Suggestion

Dans l’idéal, le code doit être mis à jour pour prévoir ce nouveau comportement du compilateur. Si vous avez besoin de l’ancienne sémantique, la variable d’itérateur peut être remplacée par une autre variable placée explicitement en dehors de la portée de la boucle.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4,5         |
| Type    | Reciblage |
