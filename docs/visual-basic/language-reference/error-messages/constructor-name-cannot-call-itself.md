---
title: Le constructeur '<name>' ne peut pas s'appeler lui-même
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409801"
---
# <a name="constructor-name-cannot-call-itself"></a>Le constructeur '\<name>' ne peut pas s'appeler lui-même
Une `Sub New` procédure dans une classe ou une structure s’appelle elle-même.  
  
 L’objectif d’un constructeur est d’initialiser une instance d’une classe ou d’une structure lorsqu’elle est créée pour la première fois. Une classe ou une structure peut avoir plusieurs constructeurs, à condition qu’ils aient tous des listes de paramètres différentes. Un constructeur est autorisé à appeler un autre constructeur pour exécuter ses fonctionnalités en plus de lui-même. Mais cela n’a pas de sens qu’un constructeur s’appelle lui-même et, en fait, cela entraînerait une récurrence infinie si elle était autorisée.  
  
 **ID d’erreur :** BC30298  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez la liste des paramètres du constructeur appelé. Elle doit être différente de celle du constructeur qui effectue l’appel.  
  
2. Si vous n’envisagez pas d’appeler un autre constructeur, supprimez `Sub New` entièrement l’appel.  
  
## <a name="see-also"></a>Voir aussi

- [Durée de vie d’un objet : création et destruction des objets](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
