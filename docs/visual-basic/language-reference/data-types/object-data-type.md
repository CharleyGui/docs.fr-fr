---
title: Type de données d’objet (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 593fda6a4949a55d77ae70edd19159a618cc6b6d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592081"
---
# <a name="object-data-type"></a>Object Data Type
Contient les adresses qui font référence aux objets. Vous pouvez affecter n’importe quel type référence (chaîne, tableau, classe ou interface) à une `Object` variable. Un `Object` variable peut également faire référence à des données de n’importe quel type valeur (numérique, `Boolean`, `Char`, `Date`, structure ou énumération).  
  
## <a name="remarks"></a>Notes  
 Le `Object` type de données peut pointer vers les données de n’importe quel type de données, y compris toute instance d’objet reconnaît votre application. Utilisez `Object` lorsque vous ne connaissez pas au moment de la compilation, le type de données la variable peut pointer vers.  
  
 La valeur par défaut `Object` est `Nothing` (une référence null).  
  
## <a name="data-types"></a>Types de données  
 Vous pouvez assigner une variable, une constante ou une expression de n’importe quel type de données à un `Object` variable. Pour déterminer le type de données un `Object` variable fait actuellement référence, vous pouvez utiliser la <xref:System.Type.GetTypeCode%2A> méthode de la <xref:System.Type?displayProperty=nameWithType> classe. L'exemple suivant illustre ce comportement.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 Le `Object` type de données est un type référence. Toutefois, Visual Basic traite une `Object` variable comme un type valeur lorsqu’elle fait référence aux données d’un type valeur.  
  
## <a name="storage"></a>Stockage  
 Tout type de données qu’il fait référence, une `Object` variable ne contient pas la valeur de données elle-même, mais plutôt un pointeur vers la valeur. Elle utilise toujours les quatre octets dans la mémoire de l’ordinateur, mais cela n’inclut pas le stockage pour les données qui représente la valeur de la variable. En raison du code qui utilise le pointeur pour localiser les données, `Object` variables contenant des types valeur sont légèrement plus lentes que celles explicitement des variables typées.  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
- **Considérations sur l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types pointeur dans d’autres environnements ne sont pas compatibles avec Visual Basic `Object` type.  
  
- **Performances** Une variable que vous déclarez avec le `Object` type est suffisamment flexible pour contenir une référence à n’importe quel objet. Toutefois, lorsque vous appelez une méthode ou propriété sur une variable de ce type, vous subissez toujours *liaison tardive* (au moment de l’exécution). Pour forcer *liaison anticipée* (au moment de la compilation) et de meilleures performances, déclarez la variable avec un nom de classe spécifique ou les convertir en type de données spécifique.  
  
     Lorsque vous déclarez une variable objet, essayez d’utiliser un type de classe spécifique, par exemple <xref:System.OperatingSystem>, au lieu du généralisée `Object` type. Vous devez également utiliser la classe la plus spécifique disponible, tel que <xref:System.Windows.Forms.TextBox> au lieu de <xref:System.Windows.Forms.Control>, de sorte que vous pouvez accéder à ses propriétés et méthodes. Vous pouvez généralement utiliser le **Classes** liste dans le **Explorateur d’objets** pour rechercher les noms de classes disponibles.  
  
- **Étendues.** Tous les types de données et tous les types référence s’étendent à la `Object` type de données. Cela signifie que vous pouvez convertir n’importe quel type à `Object` sans rencontrer un <xref:System.OverflowException?displayProperty=nameWithType> erreur.  
  
     Toutefois, si vous convertissez des types valeur et `Object`, Visual Basic effectue des opérations appelées *boxing* et *unboxing*, qui vous ralentissent l’exécution.  
  
- **Caractères de type.** `Object` n’a aucun caractère de type littéral ou un caractère de type identificateur.  
  
- **Type de Framework.** Le type correspondant dans le .NET Framework est la <xref:System.Object?displayProperty=nameWithType> classe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre une `Object` variable qui pointe vers une instance d’objet.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Object>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Guide pratique pour Déterminer si deux objets sont liés](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Guide pratique pour Déterminer si deux objets sont identiques](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
