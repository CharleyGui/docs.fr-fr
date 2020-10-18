---
title: "'<membername>' ne peut pas exposer le type '<typename>' en dehors du projet via <containertype> '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: a3972eabfe297b89c0e4d0f36943ac58e5bdf688
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162464"
---
# <a name="bc30909-membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>BC30909 : ' \<membername> 'ne peut pas exposer \<typename> le type' 'en dehors du projet via \<containertype> ' \<containertypename> '

Une variable, un paramètre de procédure ou un retour de fonction est exposé en dehors de son conteneur, mais il est déclaré en tant que type qui ne doit pas être exposé à l’extérieur du conteneur.

 Le code squelette suivant illustre une situation qui génère cette erreur.

```vb
Private Class privateClass
End Class
Public Class mainClass
    Public exposedVar As New privateClass
End Class
```

 Un type qui est déclaré `Protected` , `Friend` , `Protected Friend` ou `Private` est destiné à avoir un accès limité en dehors de son contexte de déclaration. Son utilisation en tant que type de données d’une variable avec un accès moins limité serait à l’encontre de cet objectif. Dans le code squelette précédent, `exposedVar` est `Public` et expose `privateClass` au code qui ne doit pas y avoir accès.

 **ID d’erreur :** BC30909

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Modifiez le niveau d’accès de la variable, du paramètre de procédure ou du retour de fonction pour qu’il soit au moins aussi restrictif que le niveau d’accès de son type de données.

## <a name="see-also"></a>Voir aussi

- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
