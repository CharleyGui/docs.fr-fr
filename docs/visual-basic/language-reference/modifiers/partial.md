---
title: Partial (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: da5679c3e69a938e9735922bcf4f912428024610
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642782"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Indique qu'une déclaration de type est une définition partielle du type.  
  
 Vous pouvez diviser la définition d'un type entre plusieurs déclarations à l'aide du mot clé `Partial`. Vous pouvez utiliser autant de déclarations partielles que vous le souhaitez, dans autant de fichiers sources que vous le souhaitez. Toutefois, toutes les déclarations doivent être dans le même assembly et le même espace de noms.  
  
> [!NOTE]
>  Prend en charge de Visual Basic *méthodes partielles*, qui sont généralement implémentées dans des classes partielles. Pour plus d’informations, consultez [méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) et [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attrlist`|Facultatif. Liste des attributs qui s'appliquent à ce type. Vous devez placer le [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) figurant entre crochets (`< >`).|  
|`accessmodifier`|Facultatif. Spécifie le code pouvant accéder à ce type. Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Facultatif. Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Facultatif. Consultez [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Facultatif. Consultez [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Obligatoire. Nom de ce type. Doit correspondre au nom défini dans toutes les autres déclarations partielles du même type.|  
|`Of`|Facultatif. Spécifie qu'il s'agit d'un type générique. Consultez [des Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Requis si vous utilisez [de](../../../visual-basic/language-reference/statements/of-clause.md). Consultez [tapez liste](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Facultatif. Consultez [Inherits, instruction](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Requis si vous utilisez `Inherits`. Nom de la classe ou de l'interface dont cette classe dérive.|  
|`Implements`|Facultatif. Consultez [implémente instruction](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Requis si vous utilisez `Implements`. Noms des interfaces que ce type implémente.|  
|`variabledeclarations`|Facultatif. Instructions qui déclarent des variables et des événements supplémentaires pour ce type.|  
|`proceduredeclarations`|Facultatif. Instructions qui déclarent et définissent des procédures supplémentaires pour ce type.|  
|`End Class` ou `End Structure`|Met fin à cette définition partielle de `Class` ou de `Structure`.|  
  
## <a name="remarks"></a>Notes  
 Visual Basic utilise des définitions de classe partielle pour séparer le code généré du code créé par l'utilisateur dans des fichiers sources distincts. Par exemple, le **Concepteur Windows Form** définit des classes partielles pour des contrôles tels que <xref:System.Windows.Forms.Form>. Vous ne devez pas modifier le code généré dans ces contrôles.  
  
 Toutes les règles de création de classes, structures, interfaces et modules, telles que celles relatives à l'héritage et à l'utilisation de modificateurs, s'appliquent lors de la création d'un type partiel.  
  
## <a name="best-practices"></a>Meilleures pratiques  
  
- Dans des circonstances normales, vous ne devez pas scinder le développement d'un type unique entre deux déclarations ou plus. Par conséquent, dans la plupart des cas, vous n'avez pas besoin du mot clé `Partial`.  
  
- Pour une meilleure lisibilité, chaque déclaration partielle d'un type doit inclure le mot clé `Partial`. Le compilateur permet au plus à une déclaration partielle d'omettre le mot clé. Si deux déclarations ou plus l'omettent, le compilateur signale une erreur.  
  
## <a name="behavior"></a>Comportement  
  
- **Union de déclarations.** Le compilateur traite ce type comme l'union de toutes ses déclarations partielles. Chaque modificateur issu de chaque définition partielle s'applique à l'ensemble du type, et chaque membre issu de chaque définition partielle est disponible pour l'ensemble du type.  
  
- **Promotion de type non autorisée pour les Types partiels dans les Modules.** Si une définition partielle est comprise dans un module, la promotion de type de ce type est automatiquement annulée. Dans ce cas, un ensemble de définitions partielles peut provoquer des résultats inattendus, voire même des erreurs du compilateur. Pour plus d’informations, consultez [Promotion de Type](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.  
  
 Le mot clé `Partial` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Exemple  
 L'exemple suivant fractionne la définition de la classe `sampleClass` en deux déclarations, dont chacune définit une procédure `Sub` différente.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Les deux définitions partielles de l'exemple précédent peuvent être dans le même fichier source ou dans deux fichiers sources différents.  
  
## <a name="see-also"></a>Voir aussi

- [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Promotion de type](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
