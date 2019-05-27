---
title: Débogage d’arborescences d’expression dans Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 4017e2c2592dc1d6067b428fc1d47f37775abf85
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877150"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="e38b8-102">Débogage d’arborescences d’expression dans Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="e38b8-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="e38b8-103">Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications.</span><span class="sxs-lookup"><span data-stu-id="e38b8-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="e38b8-104">Pour obtenir une vue d’ensemble rapide de l’arborescence d’expression, vous pouvez utiliser la propriété `DebugView`, qui représente des arborescences d’expression utilisant une syntaxe spéciale décrite [ci-dessous](#debugview-syntax).</span><span class="sxs-lookup"><span data-stu-id="e38b8-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="e38b8-105">(Notez que `DebugView` est disponible uniquement en mode débogage.)</span><span class="sxs-lookup"><span data-stu-id="e38b8-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView d’une arborescence d’expression dans le débogueur Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="e38b8-107">Étant donné que `DebugView` est une chaîne, vous pouvez utiliser le [visualiseur de texte intégré](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) pour l’afficher sur plusieurs lignes, en sélectionnant **Visualiseur de texte** à partir de l’icône de loupe située à côté de l’étiquette `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="e38b8-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Visualiseur de texte appliqué aux résultats de « DebugView »](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="e38b8-109">Vous pouvez également installer et utiliser [un visualiseur personnalisé](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pour les arborescences d’expression :</span><span class="sxs-lookup"><span data-stu-id="e38b8-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="e38b8-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponible sur [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), restitue l’arborescence d’expression sous forme de code C# :</span><span class="sxs-lookup"><span data-stu-id="e38b8-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Visualiseur Readable Expressions](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="e38b8-112">Le [Visualiseur Readable Expressions](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), fournit une représentation graphique de l’arborescence d’expression, ses propriétés et les objets connexes :</span><span class="sxs-lookup"><span data-stu-id="e38b8-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Visualiseur ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="e38b8-114">Pour ouvrir un visualiseur pour une arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="e38b8-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="e38b8-115">Cliquez sur l’icône de loupe qui s’affiche en regard de l’arborescence d’expression dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.</span><span class="sxs-lookup"><span data-stu-id="e38b8-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="e38b8-116">Une liste de visualiseurs disponibles s’affiche :</span><span class="sxs-lookup"><span data-stu-id="e38b8-116">A list of available visualizers is displayed.:</span></span> 

      ![Ouverture de visualiseurs à partir de Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="e38b8-118">Cliquez sur le visualiseur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e38b8-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="e38b8-119">Syntaxe `DebugView`</span><span class="sxs-lookup"><span data-stu-id="e38b8-119">`DebugView` syntax</span></span> 

<span data-ttu-id="e38b8-120">Chaque type d’expression est affiché par la propriété `DebugView`, comme décrit dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="e38b8-120">Each expression type is displayed by the `DebugView` property as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="e38b8-121">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="e38b8-121">ParameterExpressions</span></span>  
 <span data-ttu-id="e38b8-122">Les noms de variables <xref:System.Linq.Expressions.ParameterExpression> s’affichent avec le symbole "$" en préfixe.</span><span class="sxs-lookup"><span data-stu-id="e38b8-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="e38b8-123">Si un paramètre n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="e38b8-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e38b8-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="e38b8-124">Examples</span></span>  
  
|<span data-ttu-id="e38b8-125">Expression</span><span class="sxs-lookup"><span data-stu-id="e38b8-125">Expression</span></span>|<span data-ttu-id="e38b8-126">Propriété`DebugView` </span><span class="sxs-lookup"><span data-stu-id="e38b8-126">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="e38b8-127">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="e38b8-127">ConstantExpressions</span></span>  
 <span data-ttu-id="e38b8-128">Pour les objets <xref:System.Linq.Expressions.ConstantExpression> qui représentent des valeurs entières, des chaînes et des valeurs `null`, la valeur de la constante est affichée.</span><span class="sxs-lookup"><span data-stu-id="e38b8-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="e38b8-129">Pour les types numériques comportant des suffixes standard comme littéraux C#, le suffixe est ajouté à la valeur.</span><span class="sxs-lookup"><span data-stu-id="e38b8-129">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="e38b8-130">Le tableau suivant indique les suffixes associés aux différents types numériques.</span><span class="sxs-lookup"><span data-stu-id="e38b8-130">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="e38b8-131">Type</span><span class="sxs-lookup"><span data-stu-id="e38b8-131">Type</span></span>|<span data-ttu-id="e38b8-132">Suffixe</span><span class="sxs-lookup"><span data-stu-id="e38b8-132">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="e38b8-133">U</span><span class="sxs-lookup"><span data-stu-id="e38b8-133">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="e38b8-134">L</span><span class="sxs-lookup"><span data-stu-id="e38b8-134">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="e38b8-135">UL</span><span class="sxs-lookup"><span data-stu-id="e38b8-135">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="e38b8-136">D</span><span class="sxs-lookup"><span data-stu-id="e38b8-136">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="e38b8-137">F</span><span class="sxs-lookup"><span data-stu-id="e38b8-137">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="e38b8-138">M</span><span class="sxs-lookup"><span data-stu-id="e38b8-138">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="e38b8-139">Exemples</span><span class="sxs-lookup"><span data-stu-id="e38b8-139">Examples</span></span>  
  
|<span data-ttu-id="e38b8-140">Expression</span><span class="sxs-lookup"><span data-stu-id="e38b8-140">Expression</span></span>|<span data-ttu-id="e38b8-141">Propriété`DebugView` </span><span class="sxs-lookup"><span data-stu-id="e38b8-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="e38b8-142">10</span><span class="sxs-lookup"><span data-stu-id="e38b8-142">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="e38b8-143">10D</span><span class="sxs-lookup"><span data-stu-id="e38b8-143">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="e38b8-144">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="e38b8-144">BlockExpression</span></span>  
 <span data-ttu-id="e38b8-145">Si le type d’un objet <xref:System.Linq.Expressions.BlockExpression> diffère du type de la dernière expression du bloc, le type est affiché dans la propriété `DebugInfo` entre crochets pointus (\< et >).</span><span class="sxs-lookup"><span data-stu-id="e38b8-145">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="e38b8-146">Sinon, le type de l’objet <xref:System.Linq.Expressions.BlockExpression> n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="e38b8-146">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e38b8-147">Exemples</span><span class="sxs-lookup"><span data-stu-id="e38b8-147">Examples</span></span>  
  
|<span data-ttu-id="e38b8-148">Expression</span><span class="sxs-lookup"><span data-stu-id="e38b8-148">Expression</span></span>|<span data-ttu-id="e38b8-149">Propriété`DebugView` </span><span class="sxs-lookup"><span data-stu-id="e38b8-149">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="e38b8-150">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="e38b8-150">LambdaExpression</span></span>  
 <span data-ttu-id="e38b8-151">Les objets <xref:System.Linq.Expressions.LambdaExpression> sont affichés avec leurs types délégués.</span><span class="sxs-lookup"><span data-stu-id="e38b8-151"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="e38b8-152">Si une expression lambda n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="e38b8-152">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e38b8-153">Exemples</span><span class="sxs-lookup"><span data-stu-id="e38b8-153">Examples</span></span>  
  
|<span data-ttu-id="e38b8-154">Expression</span><span class="sxs-lookup"><span data-stu-id="e38b8-154">Expression</span></span>|<span data-ttu-id="e38b8-155">Propriété`DebugView` </span><span class="sxs-lookup"><span data-stu-id="e38b8-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="e38b8-156">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="e38b8-156">LabelExpression</span></span>  
 <span data-ttu-id="e38b8-157">Si vous spécifiez une valeur par défaut pour l’objet <xref:System.Linq.Expressions.LabelExpression>, cette valeur est affichée avant l’objet <xref:System.Linq.Expressions.LabelTarget>.</span><span class="sxs-lookup"><span data-stu-id="e38b8-157">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="e38b8-158">Le jeton `.Label` indique le début de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="e38b8-158">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="e38b8-159">Le jeton `.LabelTarget` indique la destination de la cible à laquelle accéder.</span><span class="sxs-lookup"><span data-stu-id="e38b8-159">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="e38b8-160">Si une étiquette n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="e38b8-160">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e38b8-161">Exemples</span><span class="sxs-lookup"><span data-stu-id="e38b8-161">Examples</span></span>  
  
|<span data-ttu-id="e38b8-162">Expression</span><span class="sxs-lookup"><span data-stu-id="e38b8-162">Expression</span></span>|<span data-ttu-id="e38b8-163">Propriété`DebugView` </span><span class="sxs-lookup"><span data-stu-id="e38b8-163">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="e38b8-164">Opérateurs Checked</span><span class="sxs-lookup"><span data-stu-id="e38b8-164">Checked Operators</span></span>  
 <span data-ttu-id="e38b8-165">Les opérateurs Checked sont affichés précédés du symbole "#".</span><span class="sxs-lookup"><span data-stu-id="e38b8-165">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="e38b8-166">Par exemple, l’opérateur d’addition checked est affiché sous la forme `#+`.</span><span class="sxs-lookup"><span data-stu-id="e38b8-166">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e38b8-167">Exemples</span><span class="sxs-lookup"><span data-stu-id="e38b8-167">Examples</span></span>  
  
|<span data-ttu-id="e38b8-168">Expression</span><span class="sxs-lookup"><span data-stu-id="e38b8-168">Expression</span></span>|<span data-ttu-id="e38b8-169">Propriété`DebugView` </span><span class="sxs-lookup"><span data-stu-id="e38b8-169">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="e38b8-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e38b8-170">See also</span></span>

- [<span data-ttu-id="e38b8-171">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="e38b8-171">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="e38b8-172">Débogage dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e38b8-172">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="e38b8-173">Créer des visualiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="e38b8-173">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
