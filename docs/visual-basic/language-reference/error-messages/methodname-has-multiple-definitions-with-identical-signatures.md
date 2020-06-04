---
title: "'<methodname>' a plusieurs définitions comportant des signatures identiques"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 3b397711cc2fb1fd0c1dfd76899b162ab5fc1542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397231"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a>'\<methodname>' a plusieurs définitions comportant des signatures identiques
Une `Function` `Sub` déclaration de procédure ou utilise le même nom de procédure et la même liste d’arguments qu’une déclaration précédente. L’une des causes possibles est une tentative de surcharge de la procédure d’origine. Les procédures surchargées doivent avoir des listes d’arguments différentes.  
  
 **ID d’erreur :** BC30269  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Modifiez le nom de la procédure ou la liste d’arguments, ou supprimez la déclaration dupliquée.  
  
## <a name="see-also"></a>Voir aussi

- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Considérations sur les surcharges de procédures](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
