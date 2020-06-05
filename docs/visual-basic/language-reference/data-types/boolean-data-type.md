---
title: Booléen (type de données)
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
ms.openlocfilehash: 851c524a83c5f24b77a151634a96798249c5905e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374419"
---
# <a name="boolean-data-type-visual-basic"></a>Booléen, type de données (Visual Basic)

Contient des valeurs qui peuvent être uniquement `True` ou `False` . Les mots clés `True` et `False` correspondent aux deux États des `Boolean` variables.  
  
## <a name="remarks"></a>Notes  

 Utilisez le [type de données booléen (Visual Basic)](boolean-data-type.md) pour contenir des valeurs à deux États telles que vrai/faux, oui/non ou activé/désactivé.  
  
 La valeur par défaut de `Boolean` est `False`.  
  
 `Boolean`les valeurs ne sont pas stockées sous forme de nombres et les valeurs stockées ne sont pas destinées à être équivalentes aux nombres. Vous ne devez jamais écrire du code qui s’appuie sur des valeurs numériques équivalentes pour `True` et `False` . Dans la mesure du possible, limitez l’utilisation des `Boolean` variables aux valeurs logiques pour lesquelles elles sont conçues.  
  
## <a name="type-conversions"></a>Conversions de type  

 Lorsque Visual Basic convertit des valeurs de type de données numériques en `Boolean` , 0 devient `False` et toutes les autres valeurs deviennent `True` . Lorsque Visual Basic convertit des `Boolean` valeurs en types numériques, `False` devient 0 et `True` devient-1.  
  
 Lorsque vous effectuez une conversion entre `Boolean` des valeurs et des types de données numériques, gardez à l’esprit que les méthodes de conversion .NET Framework ne produisent pas toujours les mêmes résultats que les mots clés de conversion Visual Basic. Cela est dû au fait que la conversion de Visual Basic conserve un comportement compatible avec les versions précédentes. Pour plus d’informations, consultez « le type booléen ne convertit pas correctement le type numérique » en [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
- **Nombres négatifs.** `Boolean`n’est pas un type numérique et ne peut pas représenter une valeur négative. Dans tous les cas, vous ne devez pas utiliser `Boolean` pour contenir des valeurs numériques.  
  
- **Caractères de type.** `Boolean`n’a aucun caractère de type de littéral ou caractère de type d’identificateur.  
  
- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Boolean?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemple  

 Dans l’exemple suivant, `runningVB` est une `Boolean` variable, qui stocke un paramètre yes/no simple.  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Boolean?displayProperty=nameWithType>
- [Types de données](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Liste des conversions](../keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType Function](../functions/ctype-function.md)
