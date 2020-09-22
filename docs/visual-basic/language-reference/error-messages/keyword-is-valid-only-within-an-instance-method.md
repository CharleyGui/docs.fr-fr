---
title: "'<keyword>' est valide uniquement dans une méthode d'instance"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: af436b8fd57ff0d2747c766a64af175760931009
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873900"
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
