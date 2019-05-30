---
title: Débogage d’arborescences d’expression dans Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 93b1b660181cd81c31055f5d30d43e535171bb55
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195984"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="76c0a-102">Débogage d’arborescences d’expression dans Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="76c0a-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="76c0a-103">Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications.</span><span class="sxs-lookup"><span data-stu-id="76c0a-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="76c0a-104">Pour obtenir un rapide aperçu de l’arborescence d’expression, vous pouvez utiliser la propriété `DebugView`, qui représente des arborescences d’expression [en utilisant une syntaxe spéciale](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="76c0a-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="76c0a-105">(Notez que `DebugView` est disponible uniquement en mode débogage.)</span><span class="sxs-lookup"><span data-stu-id="76c0a-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView d’une arborescence d’expression dans le débogueur Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="76c0a-107">Étant donné que `DebugView` est une chaîne, vous pouvez utiliser le [visualiseur de texte intégré](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) pour l’afficher sur plusieurs lignes, en sélectionnant **Visualiseur de texte** à partir de l’icône de loupe située à côté de l’étiquette `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="76c0a-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Visualiseur de texte appliqué aux résultats de « DebugView »](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="76c0a-109">Vous pouvez également installer et utiliser [un visualiseur personnalisé](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pour les arborescences d’expression, notamment :</span><span class="sxs-lookup"><span data-stu-id="76c0a-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

* <span data-ttu-id="76c0a-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponible sur [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), restitue l’arborescence d’expression sous forme de code C# :</span><span class="sxs-lookup"><span data-stu-id="76c0a-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Visualiseur Readable Expressions](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="76c0a-112">Le [Visualiseur Readable Expressions](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), fournit une représentation graphique de l’arborescence d’expression, ses propriétés et les objets connexes :</span><span class="sxs-lookup"><span data-stu-id="76c0a-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Visualiseur ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="76c0a-114">Pour ouvrir un visualiseur pour une arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="76c0a-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="76c0a-115">Cliquez sur l’icône de loupe qui s’affiche en regard de l’arborescence d’expression dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.</span><span class="sxs-lookup"><span data-stu-id="76c0a-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="76c0a-116">Une liste de visualiseurs disponibles s’affiche :</span><span class="sxs-lookup"><span data-stu-id="76c0a-116">A list of available visualizers is displayed.:</span></span> 

      ![Ouverture de visualiseurs à partir de Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="76c0a-118">Cliquez sur le visualiseur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="76c0a-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c0a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76c0a-119">See also</span></span>

- [<span data-ttu-id="76c0a-120">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="76c0a-120">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="76c0a-121">Débogage dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76c0a-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="76c0a-122">Créer des visualiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="76c0a-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="76c0a-123">`DebugView` syntaxe</span><span class="sxs-lookup"><span data-stu-id="76c0a-123">`DebugView` syntax</span></span>](debugview-syntax.md)
