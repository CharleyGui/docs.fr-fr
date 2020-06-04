---
title: "'<keyword>' est valide uniquement dans une méthode d'instance"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 537689405ea30bdd7c075320eba58a8723a93cdb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397400"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>'\<keyword>' est valide uniquement dans une méthode d'instance
Les `Me` `MyClass` `MyBase` Mots clés, et font référence à des instances de classe spécifiques. Vous ne pouvez pas les utiliser dans `Function` une `Sub` procédure ou partagée.  
  
 **ID d’erreur :** BC30043  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez le mot clé de la procédure ou supprimez le `Shared` mot clé de la déclaration de procédure.  
  
## <a name="see-also"></a>Voir aussi

- [Affectation des variables objets](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase et MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Éléments fondamentaux de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
