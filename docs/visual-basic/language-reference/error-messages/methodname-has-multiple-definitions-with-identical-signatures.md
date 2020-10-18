---
title: "'<methodname>' a plusieurs définitions comportant des signatures identiques"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 663b22421d1a0e401cfb3c135c99bd097163a78b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160364"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a>BC30269 : ' \<methodname> 'a plusieurs définitions avec des signatures identiques

Une `Function` `Sub` déclaration de procédure ou utilise le même nom de procédure et la même liste d’arguments qu’une déclaration précédente. L’une des causes possibles est une tentative de surcharge de la procédure d’origine. Les procédures surchargées doivent avoir des listes d’arguments différentes.

 **ID d’erreur :** BC30269

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Modifiez le nom de la procédure ou la liste d’arguments, ou supprimez la déclaration dupliquée.

## <a name="see-also"></a>Voir aussi

- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Considérations sur les surcharges de procédures](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
