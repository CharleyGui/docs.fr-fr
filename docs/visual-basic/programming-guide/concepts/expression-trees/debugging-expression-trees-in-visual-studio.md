---
title: Débogage d’arborescences d’expressions dans Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 3334828475ef5d933ea660ea33ae264d4ccce172
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106868"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Débogage d’arborescences d’expressions dans Visual Studio (Visual Basic)
Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications. Pour obtenir un rapide aperçu de l’arborescence d’expression, vous pouvez utiliser la propriété `DebugView`, qui représente des arborescences d’expression [en utilisant une syntaxe spéciale](debugview-syntax.md). (Notez que `DebugView` est disponible uniquement en mode débogage.)  

![DebugView d’une arborescence d’expression dans le débogueur Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

Étant donné que `DebugView` est une chaîne, vous pouvez utiliser le [visualiseur de texte intégré](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) pour l’afficher sur plusieurs lignes, en sélectionnant **Visualiseur de texte** à partir de l’icône de loupe située à côté de l’étiquette `DebugView`.

 ![Visualiseur de texte appliqué aux résultats de « DebugView »](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

Vous pouvez également installer et utiliser [un visualiseur personnalisé](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pour les arborescences d’expression, notamment :

- [Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponible sur [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), restitue l’arborescence d’expression sous forme de code C# :

  ![Visualiseur Readable Expressions](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- [Visualiseur](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) de l’arborescence de l’expression ([Licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) fournit une vue graphique de l’arborescence de l’expression, de ses propriétés et des objets associés. et peuvent restituer l’arborescence de l’expression à l’aide du code Visual Basic:

  ![Visualiseur ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Pour ouvrir un visualiseur pour une arborescence d’expressions  
  
1. Cliquez sur l’icône de loupe qui s’affiche en regard de l’arborescence d’expression dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.  
  
     Une liste de visualiseurs disponibles s’affiche : 

      ![Ouverture de visualiseurs à partir de Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. Cliquez sur le visualiseur à utiliser.  

## <a name="see-also"></a>Voir aussi

- [Arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Créer des visualiseurs personnalisés](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` syntaxe](debugview-syntax.md)
