---
title: References to Declared Elements
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 23bff2eb098982f67ecb1b709e59096d5259a644
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405181"
---
# <a name="references-to-declared-elements-visual-basic"></a>Références aux éléments déclarés (Visual Basic)
Quand votre code fait référence à un élément déclaré, le compilateur Visual Basic correspond au nom dans votre référence à la déclaration appropriée de ce nom. Si plusieurs éléments sont déclarés avec le même nom, vous pouvez contrôler lequel de ces éléments doit être référencé en *qualifiant* son nom.  
  
 Le compilateur tente de faire correspondre une référence de nom à une déclaration de nom avec l’étendue la plus *étroite*. Cela signifie qu’elle commence par le code qui fait la référence et fonctionne vers l’extérieur à travers les niveaux successifs des éléments contenants.  
  
 L’exemple suivant montre des références à deux variables portant le même nom. L’exemple déclare deux variables, chacune nommée `totalCount` , à des niveaux de portée différents dans le module `container` . Lorsque la procédure `showCount` s’affiche `totalCount` sans qualification, le compilateur Visual Basic résout la référence à la déclaration avec l’étendue la plus étroite, à savoir la déclaration locale à l’intérieur de `showCount` . Lorsqu’il est qualifié `totalCount` avec le module conteneur `container` , le compilateur résout la référence à la déclaration avec la portée plus large.  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>Qualification d’un nom d’élément  
 Si vous souhaitez remplacer ce processus de recherche et spécifier un nom déclaré dans une étendue plus large, vous devez *qualifier* le nom avec l’élément conteneur de la portée plus large. Dans certains cas, vous devrez peut-être également qualifier l’élément conteneur.  
  
 Qualifier un nom signifie le précéder dans votre instruction source avec des informations qui identifient l’emplacement de définition de l’élément cible. Ces informations sont appelées une *chaîne de qualification*. Il peut inclure un ou plusieurs espaces de noms et un module, une classe ou une structure.  
  
 La chaîne de qualification doit spécifier de manière non ambiguë le module, la classe ou la structure contenant l’élément cible. Le conteneur peut à son tour se trouver dans un autre élément contenant, généralement un espace de noms. Vous devrez peut-être inclure plusieurs éléments contenant dans la chaîne de qualification.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Pour accéder à un élément déclaré en qualifiant son nom  
  
1. Déterminez l’emplacement dans lequel l’élément a été défini. Cela peut inclure un espace de noms, ou même une hiérarchie d’espaces de noms. Dans l’espace de noms de niveau inférieur, l’élément doit être contenu dans un module, une classe ou une structure.  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. Déterminez un chemin d’accès de qualification en fonction de l’emplacement de l’élément cible. Commencez par l’espace de noms de niveau supérieur, passez à l’espace de noms de niveau le plus bas, et terminez par le module, la classe ou la structure contenant l’élément cible. Chaque élément du chemin d’accès doit contenir l’élément qui le suit.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3. Préparez la chaîne de qualification pour l’élément cible. Placez un point ( `.` ) après chaque élément dans le tracé. Votre application doit avoir accès à chaque élément de votre chaîne de qualification.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. Écrivez l’expression ou l’instruction d’assignation qui fait référence à l’élément cible de manière normale.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. Faites précéder le nom de l’élément cible de la chaîne de qualification. Le nom doit suivre immédiatement le point ( `.` ) qui suit le module, la classe ou la structure qui contient l’élément.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. Le compilateur utilise la chaîne de qualification pour rechercher une déclaration claire et non ambiguë à laquelle il peut correspondre à la référence de l’élément cible.  
  
 Vous devrez peut-être également qualifier une référence de nom si votre application a accès à plus d’un élément de programmation portant le même nom. Par exemple, les <xref:System.Windows.Forms> <xref:System.Web.UI.WebControls> espaces de noms et contiennent tous les deux une `Label` classe ( <xref:System.Windows.Forms.Label?displayProperty=nameWithType> et <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType> ). Si votre application utilise les deux, ou si elle définit sa propre `Label` classe, vous devez distinguer les différents `Label` objets. Incluez l’espace de noms ou l’alias d’importation dans la déclaration de la variable. L’exemple suivant utilise l’alias d’importation.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Membres d’autres éléments conteneur  
 Quand vous utilisez un membre non partagé d’une autre classe ou structure, vous devez d’abord qualifier le nom du membre à l’aide d’une variable ou d’une expression qui pointe vers une instance de la classe ou de la structure. Dans l’exemple suivant, `demoClass` est une instance d’une classe nommée `class1` .  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Vous ne pouvez pas utiliser le nom de la classe proprement dit pour qualifier un membre qui n’est pas [partagé](../../../language-reference/modifiers/shared.md). Vous devez d’abord créer une instance dans une variable objet (dans ce cas `demoClass` ), puis la référencer par le nom de la variable.  
  
 Si une classe ou une structure a un `Shared` membre, vous pouvez qualifier ce membre soit avec le nom de la classe ou de la structure, soit avec une variable ou une expression qui pointe vers une instance.  
  
 Un module n’a pas d’instances distinctes, et tous ses membres sont `Shared` par défaut. Par conséquent, vous qualifiez un membre de module avec le nom du module.  
  
 L’exemple suivant montre des références qualifiées à des procédures de membre de module. L’exemple déclare deux `Sub` procédures, à la fois nommées `perform` , dans différents modules d’un projet. Chacune d’elles peut être spécifiée sans qualification dans son propre module, mais elle doit être qualifiée si elle est référencée ailleurs. Étant donné que la référence finale dans `module3` n’est pas qualifiée `perform` , le compilateur ne peut pas résoudre cette référence.  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>Références aux projets  
 Pour utiliser des éléments [publics](../../../language-reference/modifiers/public.md) définis dans un autre projet, vous devez d’abord définir une *référence* à l’assembly ou la bibliothèque de types de ce projet. Pour définir une référence, cliquez sur **Ajouter une référence** dans le menu **projet** ou utilisez l’option du compilateur de ligne [de commande-Reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) .  
  
 Par exemple, vous pouvez utiliser le modèle objet XML de l' .NET Framework. Si vous définissez une référence à l' <xref:System.Xml> espace de noms, vous pouvez déclarer et utiliser l’une de ses classes, par exemple <xref:System.Xml.XmlDocument> . L'exemple suivant utilise <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Importation d’éléments contenants  
 Vous pouvez utiliser l' [instruction Imports (espace de noms et type .net)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) pour *Importer* les espaces de noms qui contiennent les modules ou les classes que vous souhaitez utiliser. Cela vous permet de faire référence aux éléments définis dans un espace de noms importé sans qualification complète de leurs noms. L’exemple suivant réécrit l’exemple précédent pour importer l' <xref:System.Xml> espace de noms.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 En outre, l' `Imports` instruction peut définir un *alias d’importation* pour chaque espace de noms importé. Cela peut rendre le code source plus concis et plus facile à lire. L’exemple suivant réécrit l’exemple précédent pour l’utiliser `xD` en tant qu’alias pour l' <xref:System.Xml> espace de noms.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 L' `Imports` instruction ne rend pas les éléments d’autres projets disponibles pour votre application. Autrement dit, il ne remplace pas la définition d’une référence. L’importation d’un espace de noms supprime simplement la nécessité de qualifier les noms définis dans cet espace de noms.  
  
 Vous pouvez également utiliser l' `Imports` instruction pour importer des modules, des classes, des structures et des énumérations. Vous pouvez ensuite utiliser les membres de ces éléments importés sans qualification. Toutefois, vous devez toujours qualifier les membres non partagés des classes et des structures à l’aide d’une variable ou d’une expression qui prend la valeur d’une instance de la classe ou de la structure.  
  
## <a name="naming-guidelines"></a>Indications concernant l'attribution d'un nom  
 Lorsque vous définissez deux ou plusieurs éléments de programmation portant le même nom, une *ambiguïté de nom* peut se produire lorsque le compilateur tente de résoudre une référence à ce nom. Si plusieurs définitions sont dans la portée, ou si aucune définition n’est dans la portée, la référence est insoluble. Pour obtenir un exemple, consultez « exemple de référence qualifiée » dans cette page d’aide.  
  
 Vous pouvez éviter toute ambiguïté de nom en attribuant à tous vos éléments des noms uniques. Vous pouvez ensuite faire référence à n’importe quel élément sans avoir à qualifier son nom avec un espace de noms, un module ou une classe. Vous réduisez également le risque de faire référence à un élément incorrect.  
  
## <a name="shadowing"></a>Copie shadow  
 Lorsque deux éléments de programmation partagent le même nom, l’un d’eux peut masquer ou *occulter*l’autre. Un élément occulté n’est pas disponible à des fins de référence ; au lieu de cela, lorsque votre code utilise le nom d’élément occulté, le compilateur Visual Basic le résout en l’élément occultant. Pour obtenir une explication plus détaillée des exemples, consultez [occultation dans Visual Basic](shadowing.md).  
  
## <a name="see-also"></a>Voir aussi

- [Declared Element Names](declared-element-names.md)
- [Caractéristiques des éléments déclarés](declared-element-characteristics.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [Variables](../variables/index.md)
- [Imports, instruction (espace de noms et type .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Nouvel opérateur](../../../language-reference/operators/new-operator.md)
- [Public](../../../language-reference/modifiers/public.md)
