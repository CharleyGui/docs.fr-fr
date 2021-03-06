---
title: La variable de portée '<variable>' masque une variable dans un bloc englobant, une variable de portée précédemment définie ou une variable déclarée implicitement dans une expression de requête
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 90fed3dd27f18fe87c326cc36dfb774822fc4b21
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162347"
---
# <a name="bc36633-range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>BC36633 : la variable \<variable> de portée masque une variable dans un bloc englobant, une variable de portée précédemment définie ou une variable déclarée implicitement dans une expression de requête

Un nom de variable de portée spécifié dans une `Select` `From` clause,, `Aggregate` ou `Let` est un doublon du nom d’une variable de portée déjà spécifiée dans la requête, ou du nom d’une variable déclarée implicitement par la requête, par exemple un nom de champ ou le nom d’une fonction d’agrégation.

 **ID d’erreur :** BC36633

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Vérifiez que toutes les variables de plage dans une étendue de requête particulière ont des noms uniques. Vous pouvez placer une requête entre parenthèses pour vous assurer que les requêtes imbriquées ont une étendue unique.

## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [From, clause](../queries/from-clause.md)
- [Clause let](../queries/let-clause.md)
- [Aggregate Clause](../queries/aggregate-clause.md)
- [Clause SELECT](../queries/select-clause.md)
