---
title: Explorer le code avec le visualiseur de syntaxe Roslyn dans Visual Studio
description: Le visualiseur de syntaxe offre un outil visuel qui permet d’explorer les modèles que le SDK .NET Compiler Platform génère pour le code.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: c7a34fda909bd044a9e65a8353d5626b533730e3
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975925"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Explorer le code avec le visualiseur de syntaxe Roslyn dans Visual Studio

Cet article fournit une vue d’ensemble de l’outil visualiseur de syntaxe inclus dans le SDK .NET Compiler Platform (« Roslyn »). Le visualiseur de syntaxe est une fenêtre Outil qui vous permet d’inspecter et d’explorer des arborescences de syntaxe. C’est un outil essentiel pour comprendre les modèles du code que vous voulez analyser. Cet outil s’avère aussi une aide précieuse au débogage quand vous développez vos propres applications à l’aide du SDK .NET Compiler Platform (« Roslyn »). Ouvrez l’outil au moment où vous créez vos premiers analyseurs. Le visualiseur facilite la compréhension des modèles utilisés par les API. Vous pouvez également utiliser des outils comme [SharpLab](https://sharplab.io) ou [LINQPad](https://www.linqpad.net/) pour inspecter du code et comprendre des arborescences de syntaxe.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Familiarisez-vous avec les concepts utilisés dans le SDK .NET Compiler Platform en lisant l’article de [vue d’ensemble](compiler-api-model.md). Celui-ci présente les arborescences de syntaxe, les nœuds, les jetons et les trivia.

## <a name="syntax-visualizer"></a>Visualiseur de syntaxe

Le **Syntax Visualizer** permet l’inspection de l’arborescence de syntaxe pour le fichier de code C# ou Visual Basic dans la fenêtre active de l’éditeur à l’intérieur de l’IDE de Visual Studio. Le visualiseur peut être lancé en cliquant sur **Afficher** > **autres fenêtres** > **Syntax Visualizer**.  Vous pouvez également utiliser la barre d’outils **Lancement rapide** dans le coin supérieur droit. Tapez « syntaxe » pour faire apparaître la commande permettant d’ouvrir le **visualiseur de syntaxe**.

Cette commande ouvre ce dernier dans une fenêtre Outil flottante. Si aucune fenêtre d’éditeur de code n’est ouverte, l’affichage est vide, comme l’illustre la figure suivante.

![Fenêtre Outil du visualiseur de syntaxe](media/syntax-visualizer/syntax-visualizer.png)

Ancrez cette fenêtre Outil à un emplacement pratique dans Visual Studio, comme le côté gauche. Le visualiseur indique des informations sur le fichier de code actuel.

Créez un projet à l’aide de la commande **fichier** > **nouveau projet** . Vous pouvez créer un projet Visual Basic ou C#. Quand Visual Studio ouvre le fichier de code principal de ce projet, le visualiseur en présente l’arborescence de syntaxe. Vous pouvez ouvrir n’importe quel fichier C#/Visual Basic existant dans cette instance de Visual Studio, et le visualiseur affiche l’arborescence de syntaxe de ce fichier. Si plusieurs fichiers de code sont ouverts dans Visual Studio, le visualiseur présente l’arborescence de syntaxe du fichier de code actif (celui qui a le focus clavier.)

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)
![Visualisation d’une arborescence de syntaxe C#](media/syntax-visualizer/visualize-csharp.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)
![Visualisation d’une arborescence de syntaxe Visual Basic](media/syntax-visualizer/visualize-visual-basic.png)

---

Comme l’illustrent les images précédentes, la fenêtre Outil du visualiseur présente l’arborescence de syntaxe en haut et une grille des propriétés en bas. La grille des propriétés présente les propriétés de l’élément actuellement sélectionné dans l’arborescence, notamment le *type* .NET et le *genre* (SyntaxKind) de l’élément.

Les arborescences de syntaxe comprennent trois types d’éléments : des *nœuds*, des *jetons* et des *trivia*. Pour en savoir plus sur ces types, lisez l’article sur l’[utilisation de la syntaxe](work-with-syntax.md). Les éléments de chaque type sont représentés à l’aide d’une couleur différente. Cliquez sur le bouton « Légende » pour obtenir une vue d’ensemble des couleurs utilisées.

Chaque élément de l’arborescence présente également sa propre **étendue**. L’**étendue** correspond aux index (position de départ et de fin) de ce nœud dans le fichier texte.  Dans le précédent exemple C#, le jeton « UsingKeyword [0..5) » a une **étendue** de cinq caractères de large, [0..5). La notation « [..) » signifie que l’index de départ fait partie de l’étendue, tandis que l’index de fin n’en fait pas partie.

Il existe deux façons de naviguer dans l’arborescence :

* Développez des éléments dans l’arborescence ou cliquez dessus. Le visualiseur sélectionne automatiquement le texte correspondant à l’étendue de cet élément dans l’éditeur de code.
* Cliquez sur le texte ou sélectionnez-le dans l’éditeur de code. Dans l’exemple précédent Visual Basic, si vous sélectionnez la ligne contenant « module Module1 » dans l’éditeur de code, le visualiseur accède automatiquement au nœud ModuleStatement correspondant dans l’arborescence.

Le visualiseur met en surbrillance l’élément dans l’arborescence dont l’étendue correspond le mieux à celle du texte sélectionné dans l’éditeur.

Le visualiseur actualise l’arborescence pour qu’elle corresponde aux modifications apportées dans le fichier de code actif. Ajoutez un appel à `Console.WriteLine()` dans `Main()`. Pendant la frappe, le visualiseur actualise l’arborescence.

Interrompez la frappe une fois vous avez tapé `Console.`. L’arborescence colore certains éléments en rose. À ce stade, il existe des erreurs (également appelées « Diagnostics ») dans le code tapé. Ces erreurs sont liées à des nœuds, des jetons et des trivia dans l’arborescence de syntaxe. Le visualiseur indique les éléments auxquels sont liées des erreurs en colorant leur arrière-plan en rose. Vous pouvez inspecter les erreurs détectées sur un élément coloré en rose en plaçant le curseur au-dessus de lui. Le visualiseur montre uniquement les erreurs syntaxiques (erreurs liées à la syntaxe du code tapé) ; il n’indique pas les erreurs sémantiques.

## <a name="syntax-graphs"></a>Graphiques de syntaxe

Cliquez avec le bouton droit sur un élément dans l’arborescence, puis cliquez sur **Afficher un graphique de syntaxe orienté**.

# <a name="c"></a>[C#](#tab/csharp)

Le visualiseur affiche une représentation graphique de la sous-arborescence dont la racine est l’élément sélectionné. Essayez ces étapes pour le nœud **MethodDeclaration** correspondant à la méthode `Main()` dans l’exemple C#. Le visualiseur affiche un graphique de syntaxe qui ressemble à celui-ci :

![Affichage d’un graphique de syntaxe C#](media/syntax-visualizer/csharp-syntax-graph.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

Essayez le même pour le nœud de sous- **bloc** correspondant `Main()` à la méthode dans l’exemple de Visual Basic précédent. Le visualiseur affiche un graphique de syntaxe qui ressemble à celui-ci :

![Affichage d’un graphique de syntaxe Visual Basic](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

La visionneuse du graphique de syntaxe contient une option permettant d’afficher une légende pour son modèle de coloration. Vous pouvez également placer le pointeur de la souris au-dessus d’éléments individuels dans le graphique de syntaxe pour afficher les propriétés correspondantes.

Vous pouvez afficher des graphiques de syntaxe pour différents éléments dans l’arborescence à plusieurs reprises. Ces graphiques s’affichent toujours dans la même fenêtre au sein de Visual Studio. Ancrez cette fenêtre à un emplacement pratique dans Visual Studio pour ne pas avoir à basculer d’un onglet à un autre afin d’afficher un nouveau graphique de syntaxe. En bas, sous les fenêtres de l’éditeur de code, s’avère souvent un emplacement pratique.

Voici la disposition d’ancrage à utiliser avec la fenêtre Outil du visualiseur et la fenêtre de graphique de syntaxe :

![Une disposition d’ancrage du visualiseur et de la fenêtre de graphique de syntaxe](media/syntax-visualizer/docking-layout.png)

Une autre option consiste à placer la fenêtre de graphique de syntaxe sur un deuxième écran, dans une configuration à double écran.

## <a name="inspecting-semantics"></a>Inspection de la sémantique

Le visualiseur de syntaxe permet une inspection rudimentaire des symboles et des informations sémantiques. Tapez `double x = 1 + 1;` au sein de Main() dans l’exemple C#. Ensuite, sélectionnez l’expression `1 + 1` dans la fenêtre de l’éditeur de code. Le visualiseur met en surbrillance le nœud **AddExpression** dans le visualiseur. Cliquez avec le bouton droit sur ce nœud **AddExpression**, puis cliquez sur **Afficher le symbole (le cas échéant)**. Notez que la plupart des éléments de menu présentent le qualificateur « le cas échéant ». Le visualiseur de syntaxe inspecte les propriétés d’un nœud, notamment celles qui ne sont éventuellement pas présentes pour tous les nœuds.

La grille des propriétés se met à jour dans le visualiseur comme l’illustre la figure suivante : le symbole de l’expression est un **SynthesizedIntrinsicOperatorSymbol** avec **Kind = Method**.

![Propriétés des symboles](media/syntax-visualizer/symbol-properties.png)

Essayez **Afficher TypeSymbol (le cas échéant)** pour le même nœud **AddExpression**. La grille des propriétés se met à jour dans le visualiseur comme l’illustre la figure suivante, en indiquant que le type de l’expression sélectionnée est `Int32`.

![Propriétés de TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

Essayez **Afficher un TypeSymbol converti (le cas échéant)** pour le même nœud **AddExpression**. La grille des propriétés se met à jour en indiquant que, bien que le type de l’expression soit `Int32`, le type converti de l’expression est `Double` comme l’illustre la figure suivante. Ce nœud inclut des informations de symbole de type converti, car l’expression `Int32` se produit dans un contexte où elle doit être convertie en `Double`. Cette conversion satisfait au type `Double` spécifié pour la variable `x` du côté gauche de l’opérateur d’assignation.

![Propriétés d’un TypeSymbol converti](media/syntax-visualizer/converted-type-symbol-properties.png)

Enfin, essayez **Afficher la valeur constante (le cas échéant)** pour le même nœud **AddExpression**. La grille des propriétés montre que la valeur de l’expression est une constante au moment de la compilation de valeur `2`.

![Valeur de constante](media/syntax-visualizer/constant-value.png)

L’exemple précédent peut également être répliqué dans Visual Basic. Tapez `Dim x As Double = 1 + 1` un fichier Visual Basic. Sélectionnez l’expression `1 + 1` dans la fenêtre de l’éditeur de code. Le visualiseur met en surbrillance le nœud **AddExpression** correspondant dans le visualiseur. Répétez les étapes précédentes pour ce nœud **AddExpression** et vous obtiendrez normalement des résultats identiques.

Examinez davantage de code dans Visual Basic. Mettez à jour votre fichier de Visual Basic principal à l’aide du code suivant :

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Ce code présente un alias nommé `C` qui se mappe sur le type `System.Console` en haut du fichier et utilise cet alias dans `Main()`. Sélectionnez l’utilisation de cet alias, le `C` dans `C.WriteLine()`, à l’intérieur de la méthode `Main()`. Le visualiseur sélectionne le nœud **IdentifierName** correspondant. Cliquez avec le bouton droit sur ce nœud et cliquez sur **Afficher le symbole (le cas échéant)**. La grille des propriétés indique que cet identificateur est lié au type `System.Console` comme l’illustre la figure suivante :

![Propriétés des symboles](media/syntax-visualizer/symbol-visual-basic.png)

Essayez **Afficher AliasSymbol (le cas échéant)** pour le même nœud **IdentifierName**. La grille des propriétés indique que l’identificateur est un alias du nom de `C` qui est lié à la cible `System.Console`. En d’autres termes, la grille des propriétés fournit des informations sur l’**AliasSymbol** correspondant à l’identificateur `C`.

![Propriétés d’un AliasSymbol](media/syntax-visualizer/alias-symbol.png)

Examinez le symbole correspondant à un type, une méthode, une propriété qui ont été déclarés. Sélectionnez le nœud correspondant dans le visualiseur et cliquez sur **Afficher le symbole (le cas échéant)**. Sélectionnez la méthode `Sub Main()`, corps de la méthode compris. Cliquez sur **Afficher le symbole (le cas échéant)** pour le nœud **SubBlock** correspondant dans le visualiseur. La grille des propriétés montre que le **MethodSymbol** de ce **SubBlock** porte le nom `Main` avec un type de retour `Void`.

![Affichage du symbole d’une déclaration de méthode](media/syntax-visualizer/method-symbol.png)

Les exemples de Visual Basic ci-dessus peuvent être facilement répliqués en C#. Tapez `using C = System.Console;` à la place de `Imports C = System.Console` pour l’alias. Les étapes précédentes en C# produisent des résultats identiques dans la fenêtre du visualiseur.

Les opérations d’inspection sémantique sont uniquement disponibles sur des nœuds. Elles ne le sont pas sur des jetons ni des trivia. Tous les nœuds ont des informations sémantiques intéressantes à inspecter. Quand un nœud n’a pas d’informations sémantiques intéressantes, le fait de cliquer sur **Afficher le symbole \* (s’il existe)** fait apparaître une grille de propriétés vide.

Pour en savoir plus sur les API permettant d’effectuer une analyse sémantique, consultez le document de vue d’ensemble de l’[utilisation de la sémantique](work-with-semantics.md).

## <a name="closing-the-syntax-visualizer"></a>Fermeture du visualiseur de syntaxe

Vous pouvez fermer la fenêtre du visualiseur quand vous ne l’utilisez pas pour examiner le code source. Le visualiseur de syntaxe met à jour son affichage au fur et à mesure que vous naviguez dans le code, en modifiant et en modifiant la source. Cela peut s’avérer perturbant quand vous ne l’utilisez pas.
