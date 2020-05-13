---
title: Débogage d’arborescences d’expressions dans Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 2c4b1fec389a8ee168b890339ce11af596581cbc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378796"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Débogage d’arborescences d’expressions dans Visual Studio (Visual Basic)
Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications. Pour obtenir un rapide aperçu de l’arborescence d’expression, vous pouvez utiliser la propriété `DebugView`, qui représente des arborescences d’expression [en utilisant une syntaxe spéciale](debugview-syntax.md). (Notez que `DebugView` est disponible uniquement en mode débogage.)  

![Capture d’écran de l’DebugView de l’arborescence de l’expression.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

Étant donné que `DebugView` est une chaîne, vous pouvez utiliser le [visualiseur de texte intégré](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) pour l’afficher sur plusieurs lignes, en sélectionnant **Visualiseur de texte** à partir de l’icône de loupe située à côté de l’étiquette `DebugView`.

 ![Capture d’écran du visualiseur de texte appliquée aux résultats de DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Vous pouvez également installer et utiliser [un visualiseur personnalisé](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pour les arborescences d’expression, notamment :

- Les [expressions lisibles](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponible au [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), affichent l’arborescence de l’expression en tant que code C# thématique, avec diverses options de rendu :

  ![Capture d’écran du visualiseur des expressions lisibles.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- Le visualiseur de l' [arborescence d’expression](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) fournit une vue graphique de l’arborescence de l’expression, de ses propriétés et des objets associés. et peuvent restituer l’arborescence de l’expression à l’aide du code Visual Basic :

  ![Capture d’écran du visualiseur ExpressionToString.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Pour ouvrir un visualiseur pour une arborescence d’expressions  
  
1. Cliquez sur l’icône de loupe qui s’affiche en regard de l’arborescence d’expression dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.  
  
    Une liste de visualiseurs disponibles s’affiche :

    ![Capture d’écran de l’ouverture des visualiseurs de l’utilisateur à partir de Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Cliquez sur le visualiseur à utiliser.  

## <a name="see-also"></a>Voir aussi

- [Arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Débogage dans Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Créer des visualiseurs personnalisés](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`stockéesyntaxe](debugview-syntax.md)
