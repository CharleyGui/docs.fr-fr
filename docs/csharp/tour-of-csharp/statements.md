---
title: Instructions C# - Visite guidée du langage C#
description: Vous créez les actions d’un programme C# à l’aide d’instructions
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159102"
---
# <a name="statements"></a>Instructions

Les actions d’un programme sont exprimées à l’aide *d’instructions*. C# prend en charge plusieurs types d’instructions, dont plusieurs sont définies en termes d’instructions incorporées.

Un *bloc* autorise l’écriture de plusieurs instructions dans les contextes où une seule instruction est autorisée. Un bloc se compose d’une liste d’instructions écrites entre les délimiteurs `{` et `}`.

Les *instructions de déclaration* sont utilisées pour déclarer des variables locales et des constantes.

Les *instructions d’expression* sont utilisées pour évaluer des expressions. Les expressions qui peuvent être utilisées en tant qu’instructions comprennent les appels de méthode, les allocations d’objet avec l’opérateur `new`, les affectations avec `=` et les opérateurs d’assignation composée, les opérations d’incrémentation et de décrémentation à l’aide des opérateurs `++` et `--` et les expressions `await`.

Les *instructions de sélection* sont utilisées pour sélectionner un nombre d’instructions possibles pour l’exécution en fonction de la valeur d’une expression. Ce groupe `if` contient `switch` les et les déclarations.

Les *instructions d’itération* servent à exécuter à plusieurs reprises une instruction incorporée. Ce groupe `while`contient `do` `for`le `foreach` , , et les déclarations.

Les *instructions de saut* sont utilisées pour transférer le contrôle. Ce groupe `break`contient `continue` `goto`le `throw` `return`, `yield` , , , et les déclarations.

L’instruction `try`...`catch` est utilisée pour intercepter les exceptions qui se produisent pendant l’exécution d’un bloc, et l’instruction `try`...`finally` permet de spécifier que le code de finalisation est toujours exécuté, qu’une exception se soit produite ou non.

Les instructions `checked` et `unchecked` permettent de contrôler le contexte de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.

L’instruction `lock` est utilisée pour obtenir le verrou d’exclusion mutuelle pour un objet donné, exécuter une instruction, puis libérer le verrou.

L’instruction `using` est utilisée pour obtenir une ressource, exécuter une instruction puis supprimer cette ressource.

La liste suivante décrit les types d’instructions qui peuvent être utilisés avec un exemple pour chacun.

* Déclaration de variable locale :

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Déclaration de constante locale :

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Instruction d’expression :

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* Instruction `if` :

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* Instruction `switch` :

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* Instruction `while` :

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* Instruction `do` :

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* Instruction `for` :

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* Instruction `foreach` :

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* Instruction `break` :

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* Instruction `continue` :

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* Instruction `goto` :

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* Instruction `return` :

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* Instruction `yield` :

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* Instructions `throw` et instructions `try` :

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* Instructions `checked` et `unchecked` :

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* Instruction `lock` :

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* Instruction `using` :

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Suivant précédent](expressions.md)
>[Next](classes-and-objects.md)
