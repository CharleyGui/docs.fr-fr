---
title: Partial
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
ms.openlocfilehash: 2482facadd0e0528ed1b71df6edb4a447947a902
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867778"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)

Indique qu'une déclaration de type est une définition partielle du type.  
  
 Vous pouvez diviser la définition d'un type entre plusieurs déclarations à l'aide du mot clé `Partial`. Vous pouvez utiliser autant de déclarations partielles que vous le souhaitez, dans autant de fichiers sources que vous le souhaitez. Toutefois, toutes les déclarations doivent être dans le même assembly et le même espace de noms.  
  
> [!NOTE]
> Visual Basic prend en charge les *méthodes partielles*, qui sont généralement implémentées dans des classes partielles. Pour plus d’informations, consultez [méthodes partielles](../../programming-guide/language-features/procedures/partial-methods.md) et [instruction Sub](../statements/sub-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`attrlist`|Optionnel. Liste des attributs qui s'appliquent à ce type. Vous devez placer la [liste des attributs](../statements/attribute-list.md) entre crochets pointus ( `< >` ).|  
|`accessmodifier`|Optionnel. Spécifie le code pouvant accéder à ce type. Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Optionnel. Consultez [Shadows](shadows.md).|  
|`MustInherit`|Optionnel. Consultez [MustInherit](mustinherit.md).|  
|`NotInheritable`|Optionnel. Voir [NotInheritable](notinheritable.md).|  
|`name`|Obligatoire. Nom de ce type. Doit correspondre au nom défini dans toutes les autres déclarations partielles du même type.|  
|`Of`|Optionnel. Spécifie qu'il s'agit d'un type générique. Consultez [types génériques dans Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Obligatoire si [vous utilisez.](../statements/of-clause.md) Consultez la [liste des types](../statements/type-list.md).|  
|`Inherits`|Optionnel. Consultez [Inherits (instruction](../statements/inherits-statement.md)).|  
|`classname`|Requis si vous utilisez `Inherits`. Nom de la classe ou de l'interface dont cette classe dérive.|  
|`Implements`|Optionnel. Consultez [Implements, instruction](../statements/implements-statement.md).|  
|`interfacenames`|Requis si vous utilisez `Implements`. Noms des interfaces que ce type implémente.|  
|`variabledeclarations`|Optionnel. Instructions qui déclarent des variables et des événements supplémentaires pour ce type.|  
|`proceduredeclarations`|Optionnel. Instructions qui déclarent et définissent des procédures supplémentaires pour ce type.|  
|`End Class` ou `End Structure`|Met fin à cette définition partielle de `Class` ou de `Structure`.|  
  
## <a name="remarks"></a>Notes  

 Visual Basic utilise des définitions de classe partielle pour séparer le code généré du code créé par l'utilisateur dans des fichiers sources distincts. Par exemple, le **Concepteur Windows Form** définit des classes partielles pour des contrôles tels que <xref:System.Windows.Forms.Form>. Vous ne devez pas modifier le code généré dans ces contrôles.  
  
 Toutes les règles de création de classes, structures, interfaces et modules, telles que celles relatives à l'héritage et à l'utilisation de modificateurs, s'appliquent lors de la création d'un type partiel.  
  
## <a name="best-practices"></a>Bonnes pratiques  
  
- Dans des circonstances normales, vous ne devez pas scinder le développement d'un type unique entre deux déclarations ou plus. Par conséquent, dans la plupart des cas, vous n'avez pas besoin du mot clé `Partial`.  
  
- Pour une meilleure lisibilité, chaque déclaration partielle d'un type doit inclure le mot clé `Partial`. Le compilateur permet au plus à une déclaration partielle d'omettre le mot clé. Si deux déclarations ou plus l'omettent, le compilateur signale une erreur.  
  
## <a name="behavior"></a>Comportement  
  
- **Union de déclarations.** Le compilateur traite ce type comme l'union de toutes ses déclarations partielles. Chaque modificateur issu de chaque définition partielle s'applique à l'ensemble du type, et chaque membre issu de chaque définition partielle est disponible pour l'ensemble du type.  
  
- **Promotion de type non autorisée pour les types partiels dans les modules.** Si une définition partielle est comprise dans un module, la promotion de type de ce type est automatiquement annulée. Dans ce cas, un ensemble de définitions partielles peut provoquer des résultats inattendus, voire même des erreurs du compilateur. Pour plus d’informations, consultez [promotion de type](../../programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.  
  
 Le mot clé `Partial` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../statements/class-statement.md)  
  
 [Structure, instruction](../statements/structure-statement.md)  
  
## <a name="example"></a>Exemple  

 L'exemple suivant fractionne la définition de la classe `sampleClass` en deux déclarations, dont chacune définit une procédure `Sub` différente.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Les deux définitions partielles de l'exemple précédent peuvent être dans le même fichier source ou dans deux fichiers sources différents.  
  
## <a name="see-also"></a>Voir aussi

- [Class (instruction)](../statements/class-statement.md)
- [Structure, instruction](../statements/structure-statement.md)
- [Promotion de type](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](shadows.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Méthodes partielles](../../programming-guide/language-features/procedures/partial-methods.md)
