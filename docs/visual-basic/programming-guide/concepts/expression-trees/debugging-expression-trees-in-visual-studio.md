---
title: Débogage d’arborescences d’expressions dans Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: a256ef852a446a189451632c87598b04c374f884
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551117"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="88141-102">Débogage d’arborescences d’expressions dans Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88141-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="88141-103">Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications.</span><span class="sxs-lookup"><span data-stu-id="88141-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="88141-104">Pour obtenir un rapide aperçu de l’arborescence d’expression, vous pouvez utiliser la propriété `DebugView`, qui représente des arborescences d’expression [en utilisant une syntaxe spéciale](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="88141-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="88141-105">(Notez que `DebugView` est disponible uniquement en mode débogage.)</span><span class="sxs-lookup"><span data-stu-id="88141-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Capture d’écran de l’DebugView de l’arborescence de l’expression.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="88141-107">Étant donné que `DebugView` est une chaîne, vous pouvez utiliser le [visualiseur de texte intégré](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) pour l’afficher sur plusieurs lignes, en sélectionnant **Visualiseur de texte** à partir de l’icône de loupe située à côté de l’étiquette `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="88141-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Capture d’écran du visualiseur de texte appliquée aux résultats de DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="88141-109">Vous pouvez également installer et utiliser [un visualiseur personnalisé](/visualstudio/debugger/create-custom-visualizers-of-data) pour les arborescences d’expression, notamment :</span><span class="sxs-lookup"><span data-stu-id="88141-109">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="88141-110">Les [expressions lisibles](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponible au [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), affichent l’arborescence de l’expression en tant que code C# thématique, avec diverses options de rendu :</span><span class="sxs-lookup"><span data-stu-id="88141-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Capture d’écran du visualiseur des expressions lisibles.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="88141-112">Le visualiseur de l' [arborescence d’expression](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([licence MIT](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) fournit une arborescence de l’arborescence de l’expression et de ses nœuds individuels. et peuvent restituer l’arborescence de l’expression à l’aide de la syntaxe Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="88141-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes; and can render the expression tree using Visual Basic syntax:</span></span>

  ![Capture d’écran du visualiseur de l’arborescence de l’expression.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="88141-114">Pour ouvrir un visualiseur pour une arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="88141-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="88141-115">Cliquez sur l’icône de loupe qui s’affiche en regard de l’arborescence d’expression dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.</span><span class="sxs-lookup"><span data-stu-id="88141-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="88141-116">Une liste de visualiseurs disponibles s’affiche :</span><span class="sxs-lookup"><span data-stu-id="88141-116">A list of available visualizers is displayed.:</span></span>

    ![Capture d’écran de l’ouverture des visualiseurs de l’utilisateur à partir de Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="88141-118">Cliquez sur le visualiseur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="88141-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="88141-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88141-119">See also</span></span>

- [<span data-ttu-id="88141-120">Arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88141-120">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="88141-121">Débogage dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88141-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="88141-122">Créer des visualiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="88141-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="88141-123">`DebugView` stockéesyntaxe</span><span class="sxs-lookup"><span data-stu-id="88141-123">`DebugView` syntax</span></span>](debugview-syntax.md)
