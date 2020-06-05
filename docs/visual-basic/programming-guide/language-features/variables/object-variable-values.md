---
title: Valeurs des variables objets
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 1dd3e8cd68086fe116daf0678a1a19881f1ae9c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410346"
---
# <a name="object-variable-values-visual-basic"></a>Valeurs des variables objets (Visual Basic)
Une variable du [type de données Object](../../../language-reference/data-types/object-data-type.md) peut faire référence à des données de n’importe quel type. La valeur que vous stockez dans une `Object` variable est conservée ailleurs en mémoire, tandis que la variable elle-même contient un pointeur vers les données.  
  
## <a name="object-classifier-functions"></a>Fonctions du classifieur d’objets  
 Visual Basic fournit des fonctions qui retournent des informations sur `Object` la référence à une variable, comme indiqué dans le tableau suivant.  
  
|Fonction|Retourne la valeur true si la variable objet fait référence à|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tableau de valeurs, plutôt qu’une valeur unique|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Une valeur de [type de données date](../../../language-reference/data-types/date-data-type.md) , ou une chaîne qui peut être interprétée comme une valeur de date et d’heure|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Objet de type <xref:System.DBNull> , qui représente des données manquantes ou inexistantes.|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Objet d’exception, qui dérive de<xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Rien](../../../language-reference/nothing.md), autrement dit, aucun objet n’est actuellement assigné à la variable|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Un nombre, ou une chaîne qui peut être interprétée comme un nombre|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Type référence (par exemple, une chaîne, un tableau, un délégué ou un type de classe)|  
  
 Vous pouvez utiliser ces fonctions pour éviter d’envoyer une valeur non valide à une opération ou à une procédure.  
  
## <a name="typeof-operator"></a>TypeOf, opérateur  
 Vous pouvez également utiliser l' [opérateur typeof](../../../language-reference/operators/typeof-operator.md) pour déterminer si une variable objet fait actuellement référence à un type de données spécifique. L' `TypeOf` expression... `Is` prend la valeur `True` si le type au moment de l’exécution de l’opérande est dérivé de ou implémente le type spécifié.  
  
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
  
 La variable objet `num` fait référence à des données de type `Integer` et `frm` fait référence à un objet de classe <xref:System.Windows.Forms.Form> .  
  
## <a name="object-arrays"></a>Tableaux d’objets  
 Vous pouvez déclarer et utiliser un tableau de `Object` variables. Cela est utile lorsque vous devez gérer une variété de types de données et de classes d’objets. Tous les éléments d’un tableau doivent avoir le même type de données déclaré. La déclaration de ce type de données `Object` vous permet de stocker des objets et des instances de classe avec d’autres types de données dans le tableau.  
  
## <a name="see-also"></a>Voir aussi

- [Variables objets](object-variables.md)
- [Déclaration des variables objets](object-variable-declaration.md)
- [Affectation des variables objets](object-variable-assignment.md)
- [Comment : référencer l'instance actuelle d'un objet](how-to-refer-to-the-current-instance-of-an-object.md)
- [Comment : déterminer le type désigné par une variable objet](how-to-determine-what-type-an-object-variable-refers-to.md)
- [Comment : déterminer si deux objets sont liés](how-to-determine-whether-two-objects-are-related.md)
- [Guide pratique : déterminer si deux objets sont identiques](how-to-determine-whether-two-objects-are-identical.md)
- [Types de données](../data-types/index.md)
