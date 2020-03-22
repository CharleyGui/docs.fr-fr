---
title: Espaces de noms
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400672"
---
# <a name="namespaces-in-visual-basic"></a>Espaces de noms dans Visual Basic
Les espaces de noms permettent d’organiser les objets définis dans un assembly. Les assemblys peuvent contenir plusieurs espaces de noms, qui peuvent à leur tour contenir d’autres espaces de noms. Les espaces de noms permettent d’éviter les ambiguïtés et de simplifier les références quand de grands groupes d’objets, tels que des bibliothèques de classes, sont utilisés.  
  
 Par exemple, le cadre .NET définit la <xref:System.Windows.Forms.ListBox> classe dans l’espace de <xref:System.Windows.Forms?displayProperty=nameWithType> nom. Le fragment de code suivant montre comment déclarer une variable en utilisant le nom qualifié complet de cette classe :  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Éviter les collisions de noms  
 .NET Les espaces nominaux du Cadre abordent un problème parfois appelé *pollution par l’espace de nom,* dans lequel le développeur d’une bibliothèque de classe est entravé par l’utilisation de noms similaires dans une autre bibliothèque. Ces conflits avec des éléments existants sont également connus sous le terme de *collisions de noms*.  
  
 Par exemple, si vous créez une classe nommée `ListBox`, vous pouvez l’utiliser dans votre projet sans qualification. Toutefois, si vous souhaitez utiliser <xref:System.Windows.Forms.ListBox> la classe cadre .NET dans le même projet, vous devez utiliser une référence entièrement qualifiée pour rendre la référence unique. Si la référence n’est pas unique, Visual Basic produit une erreur indiquant que le nom est ambigu. L’exemple de code suivant montre comment déclarer ces objets :  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 L’illustration suivante montre deux hiérarchies namespace, `ListBox`toutes deux contenant un objet nommé :  
  
 ![Capture d’écran qui montre deux hiérarchies namespace.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Par défaut, chaque fichier exécutable que vous créez avec Visual Basic contient un espace de nom du même nom que votre projet. Par exemple, si vous définissez un objet dans un projet nommé `ListBoxProject`, le fichier exécutable, ListBoxProject.exe, contient un espace de noms appelé `ListBoxProject`.  
  
 Plusieurs assemblys peuvent utiliser le même espace de noms. Visual Basic les traite comme un seul ensemble de noms. Par exemple, vous pouvez définir des classes pour un espace de noms appelé `SomeNameSpace` dans un assembly nommé `Assemb1`, et définir des classes supplémentaires pour le même espace de noms d’un assembly nommé `Assemb2`.  
  
## <a name="fully-qualified-names"></a>noms qualifiés complets  
 Les noms qualifiés complets sont des références d’objet dont le préfixe est le nom de l’espace de noms dans lequel l’objet est défini. Vous pouvez utiliser les objets définis dans d’autres projets si vous créez une référence à la classe (en choisissant **Ajouter une référence** dans le menu **Projet** ), puis utiliser le nom qualifié complet de l’objet dans votre code. Le fragment de code suivant montre comment utiliser le nom qualifié complet d’un objet provenant de l’espace de noms d’un autre projet :  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Les noms qualifiés complets empêchent les conflits de nommage, car ils permettent au compilateur d’identifier l’objet utilisé. Toutefois, les noms peuvent devenir longs et compliqués. Pour contourner ce problème, utilisez l’instruction `Imports` pour définir un *alias*, qui est un nom abrégé utilisable à la place d’un nom qualifié complet. L’exemple de code ci-dessous crée les alias de deux noms qualifiés complets, puis utilise ces alias pour définir deux objets.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Si vous utilisez l’instruction `Imports` sans alias, vous pouvez vous servir de tous les noms de l’espace de noms sans qualification, à condition qu’ils soient uniques au sein du projet. Si votre projet contient des instructions `Imports` pour les espaces de noms contenant des éléments de même nom, vous devez fournir un nom qualifié complet quand vous l’utilisez. Imaginons, par exemple, que votre projet contient les deux instructions `Imports` suivantes :  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Si vous essayez `Class1` d’utiliser sans le qualifier complètement, `Class1` Visual Basic produit une erreur indiquant que le nom est ambigu.  
  
## <a name="namespace-level-statements"></a>Instructions au niveau de l’espace de noms  
 Dans un espace de noms, vous pouvez définir des éléments tels que des modules, des interfaces, des classes, des délégués, des énumérations, des structures et d’autres espaces de noms. Vous ne pouvez pas définir d’éléments tels que des propriétés, des procédures, des variables et des événements au niveau de l’espace de noms. Ces éléments doivent être déclarés dans des conteneurs tels que des modules, des structures ou des classes.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Mot clé Global dans les noms qualifiés complets  
 Si vous avez défini une hiérarchie imbriquée d’espaces de noms, le code à l’intérieur de cette hiérarchie peut ne pas avoir accès à l’espace de noms <xref:System?displayProperty=nameWithType> de .NET Framework. L’exemple suivant illustre une hiérarchie dans laquelle l’espace de noms `SpecialSpace.System` bloque l’accès à <xref:System?displayProperty=nameWithType>.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Le compilateur Visual Basic ne peut donc pas résoudre la référence à <xref:System.Int32?displayProperty=nameWithType>, car `SpecialSpace.System` ne définit pas `Int32`. Vous pouvez utiliser le mot clé `Global` pour démarrer la chaîne de qualification au niveau le plus externe de la bibliothèque de classes du .NET Framework. Cela vous permet de spécifier l’espace de noms <xref:System?displayProperty=nameWithType> ou un autre espace de noms dans la bibliothèque de classes. L'exemple suivant illustre ce comportement.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Utilisez aussi `Global` pour accéder à d’autres espaces de noms à la racine, tels que <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, et aux espaces de noms associés à votre projet.  
  
## <a name="global-keyword-in-namespace-statements"></a>Mot clé Global dans les instructions Namespace  
 Vous pouvez également utiliser le mot clé `Global` dans une [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md). pour définir un espace de noms hors de l’espace de noms racine de votre projet.  
  
 Tous les espaces de noms dans votre projet sont basés sur l’espace de noms racine du projet.  Visual Studio définit le nom de votre projet comme espace de noms racine par défaut pour l’ensemble du code de votre projet. Par exemple, si votre projet est nommé `ConsoleApplication1`, ses éléments de programmation appartiennent à l’espace de noms `ConsoleApplication1`. Si vous déclarez `Namespace Magnetosphere`, les références à `Magnetosphere` dans le projet doivent accéder à `ConsoleApplication1.Magnetosphere`.  
  
 Les exemples suivants utilisent le mot clé `Global` pour déclarer un espace de noms hors de l’espace de noms racine du projet.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 Dans une déclaration d’espace de noms, `Global` ne peut pas être imbriqué dans un autre espace de noms.  
  
 Vous pouvez utiliser la [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) pour afficher et modifier l’ **espace de noms racine** du projet.  Pour les nouveaux projets, l’ **espace de noms racine** correspond par défaut au nom du projet. Pour définir `Global` comme espace de noms de premier niveau, effacez l’entrée **Espace de noms racine** pour que la zone soit vide. Quand l’entrée **Espace de noms racine** est effacée, vous n’avez pas besoin de spécifier le mot clé `Global` dans les déclarations d’espace de noms.  
  
 Si une instruction `Namespace` déclare un nom qui est également un espace de noms dans le .NET Framework, l’espace de noms .NET Framework n’est plus disponible si le mot clé `Global` n’est pas utilisé dans un nom qualifié complet. Pour permettre l’accès à cet espace de noms .NET Framework sans utiliser le mot clé `Global` , ajoutez le mot clé `Global` dans l’instruction `Namespace` .  
  
 Dans l’exemple suivant, le mot clé `Global` est utilisé dans la déclaration d’espace de noms `System.Text` .  
  
 En l’absence du mot clé `Global` dans la déclaration d’espace de noms, l’accès à <xref:System.Text.StringBuilder> n’est pas possible sans spécifier `Global.System.Text.StringBuilder`. Pour un projet nommé `ConsoleApplication1`, les références à `System.Text` accèdent à `ConsoleApplication1.System.Text` si le mot clé `Global` n’est pas utilisé.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Références et instruction Imports](references-and-the-imports-statement.md)
- [Imports (instruction) (espace de noms et type .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Écriture de code dans les solutions Office](/visualstudio/vsto/writing-code-in-office-solutions)
