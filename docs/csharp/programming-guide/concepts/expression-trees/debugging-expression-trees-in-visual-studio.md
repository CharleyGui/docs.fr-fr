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
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="b13cc-104">Débogage d’arborescences d’expression dans Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="b13cc-104">Debugging Expression Trees in Visual Studio (C#)</span></span>

<span data-ttu-id="b13cc-105">Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications.</span><span class="sxs-lookup"><span data-stu-id="b13cc-105">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="b13cc-106">Pour obtenir un rapide aperçu de l’arborescence d’expression, vous pouvez utiliser la propriété `DebugView`, qui représente des arborescences d’expression [en utilisant une syntaxe spéciale](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="b13cc-106">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="b13cc-107">(Notez que `DebugView` est disponible uniquement en mode débogage.)</span><span class="sxs-lookup"><span data-stu-id="b13cc-107">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Capture d’écran de l’DebugView d’une arborescence de l’expression dans le débogueur VS.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="b13cc-109">Étant donné que `DebugView` est une chaîne, vous pouvez utiliser le [visualiseur de texte intégré](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) pour l’afficher sur plusieurs lignes, en sélectionnant **Visualiseur de texte** à partir de l’icône de loupe située à côté de l’étiquette `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="b13cc-109">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Capture d’écran du visualiseur de texte appliqué aux résultats de DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="b13cc-111">Vous pouvez également installer et utiliser [un visualiseur personnalisé](/visualstudio/debugger/create-custom-visualizers-of-data) pour les arborescences d’expression, notamment :</span><span class="sxs-lookup"><span data-stu-id="b13cc-111">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="b13cc-112">Les [expressions lisibles](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponible au [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), affichent l’arborescence de l’expression en tant que code C# thématique, avec diverses options de rendu :</span><span class="sxs-lookup"><span data-stu-id="b13cc-112">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Capture d’écran du visualiseur des expressions lisibles.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="b13cc-114">Le visualiseur de l' [arborescence d’expression](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([licence MIT](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) fournit une arborescence de l’arborescence de l’expression et de ses nœuds individuels :</span><span class="sxs-lookup"><span data-stu-id="b13cc-114">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes:</span></span>

  ![Capture d’écran du visualiseur de l’arborescence de l’expression.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="b13cc-116">Pour ouvrir un visualiseur pour une arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="b13cc-116">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="b13cc-117">Cliquez sur l’icône de loupe qui s’affiche en regard de l’arborescence d’expression dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.</span><span class="sxs-lookup"><span data-stu-id="b13cc-117">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="b13cc-118">Une liste de visualiseurs disponibles s’affiche :</span><span class="sxs-lookup"><span data-stu-id="b13cc-118">A list of available visualizers is displayed.:</span></span>

    ![Capture d’écran montrant l’ouverture des visualiseurs à partir de Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="b13cc-120">Cliquez sur le visualiseur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b13cc-120">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b13cc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b13cc-121">See also</span></span>

- [<span data-ttu-id="b13cc-122">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="b13cc-122">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="b13cc-123">Débogage dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b13cc-123">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="b13cc-124">Créer des visualiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="b13cc-124">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="b13cc-125">`DebugView` stockéesyntaxe</span><span class="sxs-lookup"><span data-stu-id="b13cc-125">`DebugView` syntax</span></span>](debugview-syntax.md)
