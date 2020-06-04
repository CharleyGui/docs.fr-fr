---
title: Déclaration de variable
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 587cb84faa09b686361c255c413ad852780b8971
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410294"
---
# <a name="variable-declaration-in-visual-basic"></a>Déclaration de variable en Visual Basic
Vous déclarez une variable pour spécifier son nom et ses caractéristiques. L’instruction de déclaration pour les variables est l' [instruction Dim](../../../language-reference/statements/dim-statement.md). Son emplacement et son contenu déterminent les caractéristiques de la variable.  
  
 Pour connaître les règles et les considérations relatives au nommage des variables, consultez [noms d’éléments déclarés](../declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Niveaux de déclaration  
  
### <a name="local-and-member-variables"></a>Variables locales et de membre  
 Une *variable locale* est une variable déclarée dans une procédure. Une *variable membre* est un membre d’un type Visual Basic ; elle est déclarée au niveau du module, à l’intérieur d’une classe, d’une structure ou d’un module, mais pas dans une procédure interne à cette classe, structure ou module.  
  
### <a name="shared-and-instance-variables"></a>Variables partagées et d’instance  
 Dans une classe ou une structure, la catégorie d’une variable membre varie selon qu’elle est partagée ou non. S’il est déclaré avec le mot clé [Shared](../../../language-reference/modifiers/shared.md) , il s’agit d’une *variable partagée*, qui existe dans une seule copie partagée entre toutes les instances de la classe ou de la structure.  
  
 Dans le cas contraire, il s’agit d’une *variable d’instance*, et une copie distincte de celle-ci est créée pour chaque instance de la classe ou de la structure. Une copie donnée d’une variable d’instance est disponible uniquement pour l’instance de la classe ou de la structure dans laquelle elle a été créée. Elle est indépendante d’une copie de la variable d’instance dans une autre instance de la classe ou de la structure.  
  
## <a name="declaring-data-type"></a>Déclaration du type de données  
 La clause [As](../../../language-reference/statements/as-clause.md) dans l’instruction de déclaration vous permet de définir le type de données ou le type d’objet de la variable que vous déclarez. Vous pouvez spécifier l’un des types suivants pour une variable :  
  
- Type de données élémentaire, tel que `Boolean` , `Long` ou`Decimal`  
  
- Type de données composite, tel qu’un tableau ou une structure  
  
- Un type d’objet, ou classe, défini dans votre application ou dans une autre application  
  
- Une classe .NET Framework, telle que <xref:System.Windows.Forms.Label> ou<xref:System.Windows.Forms.TextBox>  
  
- Type d’interface, tel que <xref:System.IComparable> ou<xref:System.IDisposable>  
  
 Vous pouvez déclarer plusieurs variables dans une instruction sans avoir à répéter le type de données. Dans les instructions suivantes, les variables `i` , `j` et `k` sont déclarées en tant que type `Integer` , `l` et sous la forme `m` , et `Long` `x` et `y` comme `Single` suit :  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Pour plus d’informations sur les types de données, consultez [types de données](../data-types/index.md). Pour plus d’informations sur les objets, consultez [objets et classes](../objects-and-classes/index.md) et [programmation à l’aide de composants](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
## <a name="local-type-inference"></a>Inférence de type local  
 L' *inférence de type* est utilisée pour déterminer les types de données des variables locales déclarées sans `As` clause. Le compilateur déduit le type de la variable à partir du type de l’expression d’initialisation. Cela vous permet de déclarer des variables sans déclarer explicitement un type. Dans l’exemple suivant, `num1` et `num2` sont fortement typés en tant qu’entiers.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 Si vous souhaitez utiliser l’inférence de type local, `Option Infer` doit avoir la valeur `On` . Pour plus d’informations, consultez [Inférence de type de variable locale](local-type-inference.md) et [Option Infer, instruction](../../../language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Caractéristiques des variables déclarées  
 La durée de *vie* d’une variable est la période pendant laquelle elle peut être utilisée. En général, une variable existe tant que l’élément qui la déclare (telle qu’une procédure ou une classe) continue à exister. Si la variable n’a pas besoin de continuer à s’exécuter au-delà de la durée de vie de son élément conteneur, vous n’avez rien à faire particulier dans la déclaration. Si la variable doit continuer à exister plus longtemps que son élément conteneur, vous pouvez inclure le `Static` `Shared` mot clé ou dans son `Dim` instruction. Pour plus d’informations, consultez [durée de vie dans Visual Basic](../declared-elements/lifetime.md).  
  
 La *portée* d’une variable est l’ensemble du code qui peut y faire référence sans qualifier son nom. L’étendue d’une variable est déterminée par l’emplacement où elle est déclarée. Le code situé dans une région donnée peut utiliser les variables définies dans cette région sans avoir à qualifier leurs noms. Pour plus d'informations, consultez [Scope in Visual Basic](../declared-elements/scope.md).  
  
 Le niveau d' *accès* d’une variable est l’étendue du code qui a l’autorisation d’y accéder. Cela est déterminé par le modificateur d’accès (par exemple, [public](../../../language-reference/modifiers/public.md) ou [privé](../../../language-reference/modifiers/private.md)) que vous utilisez dans l' `Dim` instruction. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Voir aussi

- [Comment : créer une variable](how-to-create-a-new-variable.md)
- [Comment : placer des données dans et en dehors d'une variable](how-to-move-data-into-and-out-of-a-variable.md)
- [Types de données](../../../language-reference/data-types/index.md)
- [Protect](../../../language-reference/modifiers/protected.md)
- [Contact](../../../language-reference/modifiers/friend.md)
- [Statique](../../../language-reference/modifiers/static.md)
- [Caractéristiques des éléments déclarés](../declared-elements/declared-element-characteristics.md)
- [Inférence de type local](local-type-inference.md)
- [Instruction Option Infer](../../../language-reference/statements/option-infer-statement.md)
