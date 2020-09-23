---
title: Appel d'une propriété ou méthode à l'aide d'un nom de chaîne
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: 9f28548c27545d94dde38cef3e9c56f98a69b259
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086086"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Appel d'une propriété ou méthode à l'aide d'un nom de chaîne (Visual Basic)

Dans la plupart des cas, vous pouvez découvrir les propriétés et les méthodes d’un objet au moment du design, et écrire du code pour les gérer. Toutefois, dans certains cas, il se peut que vous ne connaissiez pas les propriétés et les méthodes d’un objet à l’avance, ou que vous souhaitiez simplement permettre à un utilisateur final de spécifier des propriétés ou d’exécuter des méthodes au moment de l’exécution.  
  
## <a name="callbyname-function"></a>Fonction CallByName  

 Prenons l’exemple d’une application cliente qui évalue les expressions entrées par l’utilisateur en passant un opérateur à un composant COM. Supposons que vous ajoutez constamment de nouvelles fonctions au composant qui nécessitent de nouveaux opérateurs. Lorsque vous utilisez des techniques d’accès aux objets standard, vous devez recompiler et redistribuer l’application cliente avant de pouvoir utiliser les nouveaux opérateurs. Pour éviter cela, vous pouvez utiliser la `CallByName` fonction pour passer les nouveaux opérateurs en tant que chaînes, sans modifier l’application.  
  
 La `CallByName` fonction vous permet d’utiliser une chaîne pour spécifier une propriété ou une méthode au moment de l’exécution. La signature de la `CallByName` fonction se présente comme suit :  
  
 *Result*  =  Résultat `CallByName` (*Object*, *nomprocédure*, *CallType*, *arguments*())  
  
 Le premier argument, *Object*, prend le nom de l’objet sur lequel vous souhaitez agir. L’argument *nomprocédure* prend une chaîne qui contient le nom de la méthode ou de la procédure de propriété à appeler. L’argument *CallType* prend une constante qui représente le type de procédure à appeler : une méthode ( `Microsoft.VisualBasic.CallType.Method` ), une propriété lue ( `Microsoft.VisualBasic.CallType.Get` ) ou un jeu de propriétés ( `Microsoft.VisualBasic.CallType.Set` ). L’argument *arguments* , qui est facultatif, prend un tableau de type `Object` qui contient les arguments de la procédure.  
  
 Vous pouvez utiliser `CallByName` avec les classes de votre solution actuelle, mais elle est le plus souvent utilisée pour accéder aux objets ou objets com à partir d’assemblys .NET Framework.  
  
 Supposons que vous ajoutez une référence à un assembly qui contient une classe nommée `MathClass` , qui a une nouvelle fonction nommée `SquareRoot` , comme indiqué dans le code suivant :  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 Votre application peut utiliser des contrôles de zone de texte pour contrôler la méthode qui sera appelée et ses arguments. Par exemple, si `TextBox1` contient l’expression à évaluer et `TextBox2` est utilisé pour entrer le nom de la fonction, vous pouvez utiliser le code suivant pour appeler la `SquareRoot` fonction sur l’expression dans `TextBox1` :  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 Si vous entrez « 64 » dans `TextBox1` , « SquareRoot » dans, puis que vous `TextBox2` appelez la `CallMath` procédure, la racine carrée du nombre dans `TextBox1` est évaluée. Le code de l’exemple appelle la `SquareRoot` fonction (qui prend une chaîne qui contient l’expression à évaluer comme argument requis) et retourne "8" dans `TextBox1` (la racine carrée de 64). Bien sûr, si l’utilisateur entre une chaîne non valide dans `TextBox2` , si la chaîne contient le nom d’une propriété au lieu d’une méthode, ou si la méthode avait un argument obligatoire supplémentaire, une erreur d’exécution se produit. Vous devez ajouter un code de gestion des erreurs fiable lorsque vous utilisez `CallByName` pour anticiper ces erreurs ou d’autres erreurs.  
  
> [!NOTE]
> Si la `CallByName` fonction peut être utile dans certains cas, vous devez peser son utilité sur les implications sur les performances : l’utilisation `CallByName` de pour appeler une procédure est légèrement plus lente qu’un appel à liaison tardive. Si vous appelez une fonction qui est appelée à plusieurs reprises, par exemple à l’intérieur d’une boucle, `CallByName` peut avoir un impact sérieux sur les performances.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [Détermination du type Object](determining-object-type.md)
