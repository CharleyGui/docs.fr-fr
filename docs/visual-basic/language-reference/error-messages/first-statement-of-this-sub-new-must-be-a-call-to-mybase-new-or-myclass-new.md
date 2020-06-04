---
title: La première instruction de ce 'Sub New' doit être un appel à 'MyBase.New' ou 'MyClass.New' (aucun constructeur accessible sans paramètres)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 2b9d2568fb64e4af72733ad1f3dee58aaee650e5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402977"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a>La première instruction de ce 'Sub New' doit être un appel à 'MyBase.New' ou 'MyClass.New' (aucun constructeur accessible sans paramètres)
La première instruction de ce’Sub New’doit être un appel à’MyBase. New’ou’MyClass. New', car la classe de base' \<basename> 'de' \<derivedname> 'n’a pas de’Sub New’accessible qu’il est possible d’appeler sans argument.  
  
 Dans une classe dérivée, chaque constructeur doit appeler un constructeur de classe de base ( `MyBase.New` ). Si la classe de base a un constructeur sans paramètres qui est accessible aux classes dérivées, `MyBase.New` peut être appelé automatiquement. Si ce n’est pas le cas, un constructeur de classe de base doit être appelé avec des paramètres, ce qui ne peut pas être fait automatiquement. Dans ce cas, la première instruction de chaque constructeur de classe dérivée doit appeler un constructeur paramétrable sur la classe de base, ou appeler un autre constructeur dans la classe dérivée qui effectue un appel de constructeur de classe de base.  
  
 **ID d’erreur :** BC30148  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Soit appeler `MyBase.New` en fournissant les paramètres requis, soit appeler un constructeur homologue qui effectue ce type d’appel.  
  
     Par exemple, si la classe de base a un constructeur déclaré comme `Public Sub New(ByVal index as Integer)` , la première instruction du constructeur de classe dérivée peut être `MyBase.New(100)` .  
  
## <a name="see-also"></a>Voir aussi

- [Éléments fondamentaux de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
