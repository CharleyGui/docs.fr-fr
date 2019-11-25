---
title: Dépannage des variables
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
ms.openlocfilehash: 929540788e8134760446e02c3377e78d00ca17d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351773"
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Dépannage des variables en Visual Basic
This page lists some common problems that can occur when working with variables in Visual Basic.  
  
## <a name="unable-to-access-members-of-an-object"></a>Impossible d’accéder aux membres d’un objet  
 Si votre code tente d’accéder à une propriété ou à une méthode sur un objet, il existe deux résultats possibles en cas d’erreur :  
  
- Le compilateur peut générer un message d’erreur si vous déclarez la variable objet comme étant d’un type spécifique et que vous faites ensuite référence à un membre non défini par ce type.  
  
- Une exception <xref:System.MemberAccessException> runtime se produit quand l’objet assigné à une variable objet n’expose pas le membre auquel votre code essaie d’accéder. Dans le cas d’une variable de [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md), vous pouvez également recevoir cette exception si le membre n’est pas `Public`. Cela est dû au fait que la liaison tardive autorise l’accès uniquement aux membres `Public` .  
  
 Quand l’ [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) affecte la valeur `On`à la vérification de type, une variable objet peut accéder uniquement aux méthodes et aux propriétés de la classe avec laquelle vous la déclarez. L'exemple suivant illustre ce comportement.  

 [!code-vb[VbVbalrVariables#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#2)]  
  
 Dans cet exemple, `p` peut utiliser uniquement les membres de la <xref:System.Object> classe proprement dite, qui n’incluent pas la propriété `Left` . En revanche, `q` a été déclaré comme étant de type <xref:System.Windows.Forms.Label>. Il peut donc utiliser toutes les méthodes et propriétés de la classe <xref:System.Windows.Forms.Label> dans l’espace de noms <xref:System.Windows.Forms> .  
  
### <a name="correct-approach"></a>Approche correcte  
 Pour pouvoir accéder à tous les membres d’un objet d’une classe particulière, déclarez la variable objet comme étant du type de cette classe dans la mesure du possible. Si c’est impossible, par exemple si vous ne connaissez pas le type de l’objet au moment de la compilation, vous devez affecter la valeur `Option Strict` à `Off` et déclarer la variable comme étant [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md). Cela permet d’affecter des objets de tout type à la variable, et vous devez prendre les mesures nécessaires pour vous assurer que l’objet actuellement affecté est d’un type acceptable. You can use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to make this determination.  
  
## <a name="other-components-cannot-access-your-variable"></a>D’autres composants ne peuvent pas accéder à votre variable  
 Visual Basic names are *case-insensitive*. Si deux noms diffèrent uniquement par la casse, le compilateur les interprète comme étant identiques. Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.  
  
 Toutefois, le Common Language Runtime (CLR) utilise la liaison *qui respecte la casse* . Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée. Par exemple, si vous définissez une classe avec un élément nommé `ABC`et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`. Si, par la suite, vous recompilez votre classe et que vous changez le nom de l’élément en `abc`, les autres assemblys qui utilisent votre classe ne peuvent plus accéder à cet élément. Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.  
  
 Pour plus d'informations, consultez [Common Language Runtime](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Approche correcte  
 Pour permettre à d’autres composants d’accéder à vos variables, traitez leurs noms comme s’ils respectaient la casse. Quand vous testez votre classe ou module, vérifiez que les autres assemblys se lient aux variables prévues. Une fois que vous avez publié un composant, ne modifiez pas les noms de variables existants, notamment leur casse.  
  
## <a name="wrong-variable-being-used"></a>Variable incorrecte utilisée  
 When you have more than one variable with the same name, the Visual Basic compiler attempts to resolve each reference to that name. Si les variables ont une portée différente, le compilateur résout une référence à la déclaration dont la portée est la plus petite. Si elles ont la même portée, la résolution échoue et le compilateur signale une erreur. Pour plus d'informations, consultez [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Approche correcte  
 Évitez d’utiliser des variables ayant le même nom mais une portée différente. Si vous utilisez d’autres assemblys ou projets, évitez d’utiliser des noms définis dans ces composants externes. Si plusieurs variables ont le même nom, n’oubliez pas de qualifier chaque référence à celui-ci. Pour plus d'informations, consultez [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Voir aussi

- [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Guide pratique : accéder aux membres d’un objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Guide pratique : déterminer le type désigné par une variable objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
