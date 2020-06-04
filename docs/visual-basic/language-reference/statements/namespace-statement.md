---
title: Namespace, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 0f1ba9a038fc604b6e4ede758891832e087fc096
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404432"
---
# <a name="namespace-statement"></a>Namespace, instruction
Déclare le nom d’un espace de noms et provoque la compilation du code source qui suit la déclaration dans cet espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Éléments  
 Global  
 Facultatif. Vous permet de définir un espace de noms hors de l’espace de noms racine de votre projet. Consultez [espaces de noms dans Visual Basic](../../programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Obligatoire. Nom unique qui identifie l’espace de noms. Doit être un identificateur de Visual Basic valide. Pour plus d’informations, consultez [noms d’éléments déclarés](../../programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Facultatif. Éléments qui composent l’espace de noms. Celles-ci incluent, sans s’y limiter, les énumérations, les structures, les interfaces, les classes, les modules, les délégués et d’autres espaces de noms.  
  
 `End Namespace`  
 Met fin à un `Namespace` bloc.  
  
## <a name="remarks"></a>Notes  
 Les espaces de noms sont utilisés comme système organisationnel. Ils offrent un moyen de classer et présenter les éléments de programmation exposés à d’autres programmes et applications. Notez qu’un espace de noms n’est pas un *type* dans le sens où une classe ou une structure est : vous ne pouvez pas déclarer un élément de programmation pour avoir le type de données d’un espace de noms.  
  
 Tous les éléments de programmation déclarés après une `Namespace` instruction appartiennent à cet espace de noms. Visual Basic poursuit la compilation des éléments dans le dernier espace de noms déclaré jusqu’à ce qu’il rencontre une `End Namespace` instruction ou une autre `Namespace` instruction.  
  
 Si un espace de noms est déjà défini, même en dehors de votre projet, vous pouvez y ajouter des éléments de programmation. Pour ce faire, vous utilisez une `Namespace` instruction pour diriger Visual Basic pour compiler des éléments dans cet espace de noms.  
  
 Vous pouvez utiliser une `Namespace` instruction uniquement au niveau du fichier ou de l’espace de noms. Cela signifie que le *contexte de déclaration* pour un espace de noms doit être un fichier source ou un autre espace de noms, et ne peut pas être une classe, une structure, un module, une interface ou une procédure. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).  
  
 Vous pouvez déclarer un espace de noms dans un autre. Il n’existe aucune limite stricte aux niveaux d’imbrication que vous pouvez déclarer, mais souvenez-vous que quand un autre code accède aux éléments déclarés dans l’espace de noms le plus profond, il doit utiliser une chaîne de qualification qui contient tous les noms d’espaces de noms dans la hiérarchie d’imbrication.  
  
## <a name="access-level"></a>Niveau d’accès  
 Les espaces de noms sont traités comme s’ils avaient un `Public` niveau d’accès. Un espace de noms est accessible à partir du code n’importe où dans le même projet, à partir d’autres projets qui font référence au projet et à partir de n’importe quel assembly généré à partir du projet.  
  
 Les éléments de programmation déclarés au niveau de l’espace de noms, c’est-à-dire dans un espace de noms, mais pas à l’intérieur d’un autre élément, peuvent avoir `Public` ou `Friend` accéder à. S’il n’est pas spécifié, le niveau d’accès de ce type d’élément `Friend` est utilisé par défaut. Les éléments que vous pouvez déclarer au niveau de l’espace de noms incluent des classes, des structures, des modules, des interfaces, des énumérations et des délégués. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Espace de noms racine  
 Tous les noms d’espaces de noms dans votre projet sont basés sur un *espace de noms racine*. Visual Studio définit le nom de votre projet comme espace de noms racine par défaut pour l’ensemble du code de votre projet. Par exemple, si votre projet est nommé `Payroll`, ses éléments de programmation appartiennent à l’espace de noms `Payroll`. Si vous déclarez `Namespace funding` , le nom complet de cet espace de noms est `Payroll.funding` .  
  
 Si vous souhaitez spécifier un espace de noms existant dans une `Namespace` instruction, comme dans l’exemple de classe de liste générique, vous pouvez définir votre espace de noms racine sur une valeur null. Pour ce faire, cliquez sur **Propriétés du projet** dans le menu **projet** , puis effacez l’entrée **espace de noms racine** pour que la zone soit vide. Si vous ne l’avez pas fait dans l’exemple de classe de liste générique, le compilateur Visual Basic prendrait `System.Collections.Generic` comme un nouvel espace de noms dans Project `Payroll` , avec le nom complet de `Payroll.System.Collections.Generic` .  
  
 Vous pouvez également utiliser le `Global` mot clé pour faire référence aux éléments des espaces de noms définis en dehors de votre projet. Cela vous permet de conserver le nom de votre projet en tant qu’espace de noms racine. Cela réduit le risque de fusion involontaire de vos éléments de programmation avec ceux des espaces de noms existants. Pour plus d’informations, consultez la section « mot clé global dans les noms qualifiés complets » dans [espaces de noms dans Visual Basic](../../programming-guide/program-structure/namespaces.md).  
  
 Le `Global` mot clé peut également être utilisé dans une instruction d’espace de noms. pour définir un espace de noms hors de l’espace de noms racine de votre projet. Pour plus d’informations, consultez la section « mot clé global dans les instructions d’espace de noms » dans [espaces de noms dans Visual Basic](../../programming-guide/program-structure/namespaces.md).  
  
 **Dépannage.** L’espace de noms racine peut entraîner des concaténations inattendues de noms d’espaces de noms. Si vous faites référence à des espaces de noms définis en dehors de votre projet, le compilateur Visual Basic peut les interpréter comme des espaces de noms imbriqués dans l’espace de noms racine. Dans ce cas, le compilateur ne reconnaît pas les types qui ont déjà été définis dans les espaces de noms externes. Pour éviter cela, affectez à votre espace de noms racine une valeur null, comme décrit dans « espace de noms racine », ou utilisez le `Global` mot clé pour accéder aux éléments des espaces de noms externes.  
  
## <a name="attributes-and-modifiers"></a>Attributs et modificateurs  
 Vous ne pouvez pas appliquer d’attributs à un espace de noms. Un attribut fournit des informations aux métadonnées de l’assembly, ce qui n’est pas significatif pour les classifieurs sources tels que les espaces de noms.  
  
 Vous ne pouvez pas appliquer de modificateurs d’accès ou de procédures, ni d’autres modificateurs, à un espace de noms. Étant donné qu’il ne s’agit pas d’un type, ces modificateurs ne sont pas significatifs.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare deux espaces de noms, l’un imbriqué dans l’autre.  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare plusieurs espaces de noms imbriqués sur une seule ligne, et équivaut à l’exemple précédent.  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant accède à la classe définie dans les exemples précédents.  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit la structure d’une nouvelle classe de liste générique et l’ajoute à l' <xref:System.Collections.Generic?displayProperty=nameWithType> espace de noms.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Voir aussi

- [Imports, instruction (espace de noms et type .NET)](imports-statement-net-namespace-and-type.md)
- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Espaces de noms dans Visual Basic](../../programming-guide/program-structure/namespaces.md)
