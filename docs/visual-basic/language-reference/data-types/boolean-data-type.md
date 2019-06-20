---
title: Booléen, type de données (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: b1e4add39cee6c733a6f4b95aa1668975f2f2d6d
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268257"
---
# <a name="boolean-data-type-visual-basic"></a>Booléen, type de données (Visual Basic)
Contient les valeurs qui peuvent être uniquement `True` ou `False`. Les mots clés `True` et `False` correspondent aux deux États de `Boolean` variables.  
  
## <a name="remarks"></a>Notes  
 Utilisez le [Type de données booléen (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) destiné à contenir les valeurs de deux États tels que vrai/faux, Oui/Non, ou désactivez-les.  
  
 La valeur par défaut de `Boolean` est `False`.  
  
 `Boolean` les valeurs ne sont pas stockées sous forme de nombres et les valeurs stockées ne sont pas destinées à être équivalentes aux nombres. Vous devez jamais écrire du code qui s’appuie sur des valeurs numériques équivalentes pour `True` et `False`. Si possible, vous devez limiter l’utilisation de `Boolean` variables aux valeurs logiques pour lesquelles elles sont conçues.  
  
## <a name="type-conversions"></a>Conversions de type  
 Lorsque Visual Basic convertit les valeurs de type de données numériques à `Boolean`, 0 devient `False` et toutes les autres valeurs deviennent `True`. Lorsque Visual Basic convertit `Boolean` valeurs en types numériques, `False` devient 0 et `True` devient -1.  
  
 Lorsque vous effectuez une conversion entre `Boolean` valeurs et types de données numériques, n’oubliez pas que les méthodes de conversion de .NET Framework ne produisent pas toujours les mêmes résultats que les mots clés de conversion Visual Basic. Il s’agit, car la conversion Visual Basic conserve un comportement compatible avec les versions précédentes. Pour plus d’informations, consultez « Le Type booléenne ne se convertit pas correctement en Type numérique » dans [dépannage des Types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
- **Nombres négatifs.** `Boolean` n’est pas un type numérique et ne peut pas représenter une valeur négative. Dans tous les cas, vous ne devez pas utiliser `Boolean` pour contenir des valeurs numériques.  
  
- **Caractères de type.** `Boolean` n’a aucun caractère de type littéral ou un caractère de type identificateur.  
  
- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Boolean?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `runningVB` est un `Boolean` variable, qui enregistre une simple valeur yes/no.  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Boolean?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)
