---
title: Valeurs des variables objets (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 728f097b3c084e5292cb2d2bf5a0c1d20bdad922
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004588"
---
# <a name="object-variable-values-visual-basic"></a>Valeurs des variables objets (Visual Basic)
Une variable du [type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) peut faire référence à des données de n’importe quel type. La valeur que vous stockez dans une variable de `Object` est conservée ailleurs en mémoire, tandis que la variable elle-même contient un pointeur vers les données.  
  
## <a name="object-classifier-functions"></a>Fonctions du classifieur d’objets  
 Visual Basic fournit des fonctions qui retournent des informations sur la référence à une variable de `Object`, comme indiqué dans le tableau suivant.  
  
|Fonction|Retourne la valeur true si la variable objet fait référence à|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tableau de valeurs, plutôt qu’une valeur unique|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Une valeur de [type de données date](../../../../visual-basic/language-reference/data-types/date-data-type.md) , ou une chaîne qui peut être interprétée comme une valeur de date et d’heure|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Objet de type <xref:System.DBNull>, qui représente des données manquantes ou inexistantes.|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Objet d’exception, qui dérive de <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Rien](../../../../visual-basic/language-reference/nothing.md), autrement dit, aucun objet n’est actuellement assigné à la variable|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Un nombre, ou une chaîne qui peut être interprétée comme un nombre|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Type référence (par exemple, une chaîne, un tableau, un délégué ou un type de classe)|  
  
 Vous pouvez utiliser ces fonctions pour éviter d’envoyer une valeur non valide à une opération ou à une procédure.  
  
## <a name="typeof-operator"></a>TypeOf, opérateur  
 Vous pouvez également utiliser l' [opérateur typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si une variable objet fait actuellement référence à un type de données spécifique. L’expression `TypeOf`...`Is` prend la valeur `True` si le type au moment de l’exécution de l’opérande est dérivé de ou implémente le type spécifié.  
  
 L’exemple suivant utilise `TypeOf` sur les variables objets qui font référence aux types valeur et référence.  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 L’exemple précédent écrit les lignes suivantes dans la fenêtre de **débogage** :  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 La variable objet `num` fait référence à des données de type `Integer`, et `frm` fait référence à un objet de la classe <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Tableaux d’objets  
 Vous pouvez déclarer et utiliser un tableau de variables `Object`. Cela est utile lorsque vous devez gérer une variété de types de données et de classes d’objets. Tous les éléments d’un tableau doivent avoir le même type de données déclaré. Déclarer ce type de données comme `Object` vous permet de stocker des objets et des instances de classe avec d’autres types de données dans le tableau.  
  
## <a name="see-also"></a>Voir aussi

- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Guide pratique : référencer l'instance actuelle d'un objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Guide pratique : déterminer le type désigné par une variable objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Guide pratique : déterminer si deux objets sont liés](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Guide pratique : déterminer si deux objets sont identiques](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
