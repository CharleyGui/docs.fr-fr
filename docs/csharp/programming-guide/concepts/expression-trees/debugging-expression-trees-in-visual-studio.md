---
title: Débogage d’arborescences d’expression dans Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 43091d11dfc1fae3e6f047f35b61e992c5aaf50b
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104909"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Débogage d’arborescences d’expression dans Visual Studio (C#)
Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications. Pour obtenir un rapide aperçu de l’arborescence d’expression, vous pouvez utiliser la propriété `DebugView`, qui représente des arborescences d’expression [en utilisant une syntaxe spéciale](debugview-syntax.md). (Notez que `DebugView` est disponible uniquement en mode débogage.)  

![DebugView d’une arborescence d’expression dans le débogueur Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

Étant donné que `DebugView` est une chaîne, vous pouvez utiliser le [visualiseur de texte intégré](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) pour l’afficher sur plusieurs lignes, en sélectionnant **Visualiseur de texte** à partir de l’icône de loupe située à côté de l’étiquette `DebugView`.

 ![Visualiseur de texte appliqué aux résultats de « DebugView »](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Vous pouvez également installer et utiliser [un visualiseur personnalisé](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pour les arborescences d’expression, notamment :

- [Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponible sur [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), restitue l’arborescence d’expression sous forme de code C# :

  ![Visualiseur Readable Expressions](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- Le [Visualiseur Readable Expressions](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), fournit une représentation graphique de l’arborescence d’expression, ses propriétés et les objets connexes :

  ![Visualiseur ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Pour ouvrir un visualiseur pour une arborescence d’expressions  
  
1. Cliquez sur l’icône de loupe qui s’affiche en regard de l’arborescence d’expression dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.  
  
     Une liste de visualiseurs disponibles s’affiche : 

      ![Ouverture de visualiseurs à partir de Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Cliquez sur le visualiseur à utiliser.  
  
## <a name="see-also"></a>Voir aussi

- [Arborescences d’expressions (C#)](./index.md)
- [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Créer des visualiseurs personnalisés](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` syntaxe](debugview-syntax.md)
