---
title: Débogage d’arborescences d’expression dans Visual Studio (C#)
description: En savoir plus sur la propriété DebugView dans Visual Studio. Découvrez comment utiliser cette propriété pour analyser la structure et le contenu des arborescences d’expressions.
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 5dcf56f96ecdbfdc3f4cb171fdb30b96456b59c9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154130"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Débogage d’arborescences d’expression dans Visual Studio (C#)

Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications. Pour obtenir un rapide aperçu de l’arborescence d’expression, vous pouvez utiliser la propriété `DebugView`, qui représente des arborescences d’expression [en utilisant une syntaxe spéciale](debugview-syntax.md). (Notez que `DebugView` est disponible uniquement en mode débogage.)  

![Capture d’écran de l’DebugView d’une arborescence de l’expression dans le débogueur VS.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

Étant donné que `DebugView` est une chaîne, vous pouvez utiliser le [visualiseur de texte intégré](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) pour l’afficher sur plusieurs lignes, en sélectionnant **Visualiseur de texte** à partir de l’icône de loupe située à côté de l’étiquette `DebugView`.

 ![Capture d’écran du visualiseur de texte appliqué aux résultats de DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

Vous pouvez également installer et utiliser [un visualiseur personnalisé](/visualstudio/debugger/create-custom-visualizers-of-data) pour les arborescences d’expression, notamment :

- Les [expressions lisibles](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponible au [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), affichent l’arborescence de l’expression en tant que code C# thématique, avec diverses options de rendu :

  ![Capture d’écran du visualiseur des expressions lisibles.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- Le visualiseur de l' [arborescence d’expression](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([licence MIT](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) fournit une arborescence de l’arborescence de l’expression et de ses nœuds individuels :

  ![Capture d’écran du visualiseur de l’arborescence de l’expression.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Pour ouvrir un visualiseur pour une arborescence d’expressions  
  
1. Cliquez sur l’icône de loupe qui s’affiche en regard de l’arborescence d’expression dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.  

    Une liste de visualiseurs disponibles s’affiche :

    ![Capture d’écran montrant l’ouverture des visualiseurs à partir de Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. Cliquez sur le visualiseur à utiliser.  
  
## <a name="see-also"></a>Voir aussi

- [Arborescences d’expressions (C#)](./index.md)
- [Débogage dans Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Créer des visualiseurs personnalisés](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` stockéesyntaxe](debugview-syntax.md)
