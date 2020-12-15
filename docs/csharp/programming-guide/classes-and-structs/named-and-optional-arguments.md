---
title: Arguments nommés et facultatifs - Guide de programmation C#
description: Les arguments nommés en C# spécifient des arguments par nom, et non par position. Les arguments facultatifs peuvent être omis.
ms.date: 09/25/2020
ms.custom: contperf-fy21q1
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: bb79d956124a610bac0de6825c1f42655789e98d
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513105"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="8ac0c-104">Arguments nommés et facultatifs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8ac0c-104">Named and Optional Arguments (C# Programming Guide)</span></span>

<span data-ttu-id="8ac0c-105">C# 4 introduit des arguments nommés et facultatifs.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-105">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="8ac0c-106">Les *arguments nommés* vous permettent de spécifier un argument pour un paramètre en faisant correspondre l’argument avec son nom plutôt qu’avec sa position dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-106">*Named arguments* enable you to specify an argument for a parameter by matching the argument with its name rather than with its position in the parameter list.</span></span> <span data-ttu-id="8ac0c-107">Les *arguments facultatifs* vous permettent d’omettre des arguments pour certains paramètres.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-107">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="8ac0c-108">Les deux techniques peuvent être utilisées avec les méthodes, les indexeurs, les constructeurs et les délégués.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-108">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>

<span data-ttu-id="8ac0c-109">Quand vous utilisez des arguments nommés et facultatifs, ils sont évalués selon leur ordre d’affichage dans la liste d’arguments, et non dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-109">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>

<span data-ttu-id="8ac0c-110">Les paramètres nommés et facultatifs vous permettent de fournir des arguments pour les paramètres sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-110">Named and optional parameters enable you to supply arguments for selected parameters.</span></span> <span data-ttu-id="8ac0c-111">Cette fonctionnalité simplifie les appels aux interfaces COM, telles que les API Microsoft Office Automation.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-111">This capability greatly eases calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="8ac0c-112">Arguments nommés</span><span class="sxs-lookup"><span data-stu-id="8ac0c-112">Named Arguments</span></span>

<span data-ttu-id="8ac0c-113">Les arguments nommés vous libèrent de l’ordre des paramètres dans les listes de paramètres des méthodes appelées.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-113">Named arguments free you from matching the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="8ac0c-114">Vous pouvez spécifier le paramètre de chaque argument par son nom.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-114">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="8ac0c-115">Par exemple, une fonction qui imprime les détails d’une commande (par exemple, le nom du vendeur, le numéro de commande & nom du produit) peut être appelée en envoyant des arguments par position, dans l’ordre défini par la fonction.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-115">For example, a function that prints order details (such as, seller name, order number & product name) can be called by sending arguments by position, in the order defined by the function.</span></span>

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

<span data-ttu-id="8ac0c-116">Si vous ne vous souvenez pas de l’ordre des paramètres, mais que vous connaissez leur nom, vous pouvez envoyer les arguments dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-116">If you don't remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

<span data-ttu-id="8ac0c-117">Les arguments nommés améliorent également la lisibilité de votre code en identifiant ce que chaque argument représente.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-117">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="8ac0c-118">Dans l’exemple de méthode ci-dessous, l' `sellerName` ne peut pas être null ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-118">In the example method below, the `sellerName` can't be null or white space.</span></span> <span data-ttu-id="8ac0c-119">`sellerName` et `productName` étant tous deux des types de chaînes, au lieu d’envoyer les arguments par position, il est plus logique d’utiliser des arguments nommés pour lever l’ambiguïté entre les deux et réduire les risques de confusion pour toute personne lisant le code.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-119">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
<span data-ttu-id="8ac0c-120">Les arguments nommés, quand ils sont utilisés avec des arguments de position, sont valides tant que :</span><span class="sxs-lookup"><span data-stu-id="8ac0c-120">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="8ac0c-121">Ils ne sont pas suivis d’arguments de position, ou</span><span class="sxs-lookup"><span data-stu-id="8ac0c-121">they're not followed by any positional arguments, or</span></span>

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- <span data-ttu-id="8ac0c-122">_À compter de C# 7.2_, ils sont utilisés dans la position correcte</span><span class="sxs-lookup"><span data-stu-id="8ac0c-122">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="8ac0c-123">Dans l’exemple ci-dessous, le paramètre `orderNum` est à la position correcte, mais il n’est pas explicitement nommé.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-123">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

<span data-ttu-id="8ac0c-124">Les arguments positionnels qui suivent les arguments nommés non ordonnés ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-124">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a><span data-ttu-id="8ac0c-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ac0c-125">Example</span></span>

<span data-ttu-id="8ac0c-126">Le code suivant implémente les exemples de cette section, ainsi que d’autres exemples.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-126">The following code implements the examples from this section along with some additional ones.</span></span>  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a><span data-ttu-id="8ac0c-127">Arguments facultatifs</span><span class="sxs-lookup"><span data-stu-id="8ac0c-127">Optional Arguments</span></span>

<span data-ttu-id="8ac0c-128">La définition d’une méthode, d’un constructeur, d’un indexeur ou d’un délégué peut spécifier que ses paramètres sont obligatoires ou facultatifs.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-128">The definition of a method, constructor, indexer, or delegate can specify its parameters are required or optional.</span></span> <span data-ttu-id="8ac0c-129">Chaque appel doit fournir des arguments pour tous les paramètres obligatoires, mais peut omettre les arguments des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-129">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>

<span data-ttu-id="8ac0c-130">Dans sa définition, chaque paramètre facultatif a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-130">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="8ac0c-131">Si aucun argument n’est envoyé pour ce paramètre, la valeur par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-131">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="8ac0c-132">Une valeur par défaut doit être l’un des types d’expressions suivants :</span><span class="sxs-lookup"><span data-stu-id="8ac0c-132">A default value must be one of the following types of expressions:</span></span>
  
- <span data-ttu-id="8ac0c-133">une expression constante ;</span><span class="sxs-lookup"><span data-stu-id="8ac0c-133">a constant expression;</span></span>  
- <span data-ttu-id="8ac0c-134">une expression de la forme `new ValType()`, où `ValType` est un type valeur (par exemple, [enum](../../language-reference/builtin-types/enum.md) ou [struct](../../language-reference/builtin-types/struct.md)) ;</span><span class="sxs-lookup"><span data-stu-id="8ac0c-134">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>
- <span data-ttu-id="8ac0c-135">une expression de la forme [default(ValType)](../../language-reference/operators/default.md), où `ValType` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-135">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>

<span data-ttu-id="8ac0c-136">Les paramètres facultatifs sont définis à la fin de la liste de paramètres, après tous les paramètres obligatoires.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-136">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="8ac0c-137">Si l’appelant fournit un argument pour l’un des paramètres d’une série de paramètres facultatifs, il doit fournir des arguments pour tous les paramètres facultatifs précédents.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-137">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="8ac0c-138">Les écarts séparés par des virgules dans la liste d’arguments ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-138">Comma-separated gaps in the argument list aren't supported.</span></span> <span data-ttu-id="8ac0c-139">Par exemple, dans le code suivant, la méthode d’instance `ExampleMethod` est définie avec un paramètre obligatoire et deux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-139">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

<span data-ttu-id="8ac0c-140">L’appel suivant à `ExampleMethod` provoque une erreur du compilateur, car un argument est fourni pour le troisième paramètre, mais pas pour le deuxième.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-140">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>

```csharp
//anExample.ExampleMethod(3, ,4);
```

<span data-ttu-id="8ac0c-141">Toutefois, si vous connaissez le nom du troisième paramètre, vous pouvez utiliser un argument nommé pour effectuer la tâche.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-141">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

<span data-ttu-id="8ac0c-142">IntelliSense indique les paramètres facultatifs par des crochets, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8ac0c-142">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>

![Capture d’écran montrant l’info express IntelliSense pour la méthode ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> <span data-ttu-id="8ac0c-144">Vous pouvez aussi déclarer des paramètres facultatifs à l’aide de la classe <xref:System.Runtime.InteropServices.OptionalAttribute> .NET.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-144">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="8ac0c-145">Les paramètres `OptionalAttribute` ne nécessitent pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-145">`OptionalAttribute` parameters do not require a default value.</span></span>

## <a name="example"></a><span data-ttu-id="8ac0c-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ac0c-146">Example</span></span>

<span data-ttu-id="8ac0c-147">Dans l’exemple suivant, le constructeur associé à `ExampleClass` a un seul paramètre, qui est facultatif.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-147">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="8ac0c-148">La méthode d’instance `ExampleMethod` a un paramètre obligatoire (`required`) et deux paramètres facultatifs (`optionalstr` et `optionalint`).</span><span class="sxs-lookup"><span data-stu-id="8ac0c-148">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="8ac0c-149">Le code dans `Main` montre les différentes façons dont le constructeur et la méthode peuvent être appelés.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-149">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

<span data-ttu-id="8ac0c-150">Le code précédent illustre un certain nombre d’exemples où les paramètres facultatifs ne sont pas appliqués correctement.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-150">The preceding code shows a number of examples where optional parameters aren't applied correctly.</span></span> <span data-ttu-id="8ac0c-151">Le premier illustre qu’un argument doit être fourni pour le premier paramètre, ce qui est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-151">The first illustrates that an argument must be supplied for the first parameter, which is required.</span></span>
  
## <a name="com-interfaces"></a><span data-ttu-id="8ac0c-152">Interfaces COM</span><span class="sxs-lookup"><span data-stu-id="8ac0c-152">COM Interfaces</span></span>

<span data-ttu-id="8ac0c-153">Les arguments nommés et facultatifs, ainsi que la prise en charge des objets dynamiques, améliorent beaucoup l’interopérabilité avec les API COM, telles que les API d’automatisation d’Office.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-153">Named and optional arguments, along with support for dynamic objects, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>

<span data-ttu-id="8ac0c-154">Par exemple, la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> de l’interface <xref:Microsoft.Office.Interop.Excel.Range> de Microsoft Office Excel comporte sept paramètres, tous facultatifs.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-154">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="8ac0c-155">Ces paramètres sont indiqués dans l’illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="8ac0c-155">These parameters are shown in the following illustration:</span></span>

![Capture d’écran montrant l’info express IntelliSense pour la méthode AutoFormat.](./media/named-and-optional-arguments/autoformat-method-parameters.png)

<span data-ttu-id="8ac0c-157">Dans C# 3.0 et les versions antérieures, un argument est obligatoire pour chaque paramètre, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-157">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

<span data-ttu-id="8ac0c-158">Toutefois, vous pouvez considérablement simplifier l’appel à `AutoFormat` en utilisant les arguments nommés et facultatifs introduits dans C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-158">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="8ac0c-159">Les arguments nommés et facultatifs vous permettent d’omettre l’argument d’un paramètre facultatif si vous ne souhaitez pas modifier la valeur par défaut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-159">Named and optional arguments enable you to omit the argument for an optional parameter if you don't want to change the parameter's default value.</span></span> <span data-ttu-id="8ac0c-160">Dans l’appel suivant, une valeur est spécifiée pour un seul des sept paramètres.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-160">In the following call, a value is specified for only one of the seven parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

<span data-ttu-id="8ac0c-161">Pour plus d’informations et d’exemples, consultez [comment utiliser des arguments nommés et facultatifs dans la programmation Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) et [Comment accéder aux objets Office Interop à l’aide des fonctionnalités C#](../interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="8ac0c-161">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>
  
## <a name="overload-resolution"></a><span data-ttu-id="8ac0c-162">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="8ac0c-162">Overload Resolution</span></span>

<span data-ttu-id="8ac0c-163">L’utilisation d’arguments nommés et facultatifs affecte la résolution de surcharge des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="8ac0c-163">Use of named and optional arguments affects overload resolution in the following ways:</span></span>

- <span data-ttu-id="8ac0c-164">Une méthode, un indexeur ou un constructeur est un candidat pour l’exécution si chacun de ses paramètres est facultatif ou correspond, par nom ou par position, à un seul argument dans l’instruction appelante, et que cet argument peut être converti vers le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-164">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
- <span data-ttu-id="8ac0c-165">Si plusieurs candidats sont trouvés, les règles de résolution de surcharge des conversions préférées sont appliquées aux arguments qui sont explicitement spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-165">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="8ac0c-166">Les arguments omis pour les paramètres facultatifs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-166">Omitted arguments for optional parameters are ignored.</span></span>
- <span data-ttu-id="8ac0c-167">Si deux candidats sont jugés corrects, la préférence passe à un candidat qui n’a pas de paramètres facultatifs pour lesquels des arguments ont été omis dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-167">If two candidates are judged to be equally good, preference goes to a candidate that doesn't have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="8ac0c-168">La résolution de surcharge préfère généralement les candidats qui ont moins de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8ac0c-168">Overload resolution generally prefers candidates that have fewer parameters.</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="8ac0c-169">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8ac0c-169">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
