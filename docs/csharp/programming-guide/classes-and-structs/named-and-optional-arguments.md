---
title: Arguments nommés et facultatifs - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
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
ms.openlocfilehash: 74cfc6a425e82014bbcf5093f52f476ff09db130
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796562"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="96602-102">Arguments nommés et facultatifs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="96602-102">Named and Optional Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="96602-103">C# 4 introduit des arguments nommés et facultatifs.</span><span class="sxs-lookup"><span data-stu-id="96602-103">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="96602-104">Les *arguments nommés* vous permettent de spécifier un argument pour un paramètre particulier en associant l’argument avec le nom du paramètre plutôt qu’avec la position du paramètre dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="96602-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="96602-105">Les *arguments facultatifs* vous permettent d’omettre des arguments pour certains paramètres.</span><span class="sxs-lookup"><span data-stu-id="96602-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="96602-106">Les deux techniques peuvent être utilisées avec les méthodes, les indexeurs, les constructeurs et les délégués.</span><span class="sxs-lookup"><span data-stu-id="96602-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="96602-107">Quand vous utilisez des arguments nommés et facultatifs, ils sont évalués selon leur ordre d’affichage dans la liste d’arguments, et non dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="96602-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="96602-108">La combinaison de paramètres nommés et facultatifs vous permet de fournir des arguments uniquement pour certains paramètres d’une liste de paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="96602-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="96602-109">Cette fonctionnalité facilite considérablement les appels aux interfaces COM telles que les API Microsoft Office Automation.</span><span class="sxs-lookup"><span data-stu-id="96602-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="96602-110">Arguments nommés</span><span class="sxs-lookup"><span data-stu-id="96602-110">Named Arguments</span></span>  
 <span data-ttu-id="96602-111">Avec les arguments nommés, vous n’avez plus à mémoriser ou à rechercher l’ordre des paramètres dans les listes de paramètres des méthodes appelées.</span><span class="sxs-lookup"><span data-stu-id="96602-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="96602-112">Vous pouvez spécifier le paramètre de chaque argument par son nom.</span><span class="sxs-lookup"><span data-stu-id="96602-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="96602-113">Par exemple, une fonction qui imprime les détails d’une commande (par exemple, le nom du vendeur, le nom du produit et le numéro de commande) peut être appelée de manière standard en envoyant des arguments par position, dans l’ordre défini par la fonction.</span><span class="sxs-lookup"><span data-stu-id="96602-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="96602-114">Si vous ne vous souvenez pas de l’ordre des paramètres, mais que vous connaissez leur nom, vous pouvez envoyer les arguments dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="96602-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="96602-115">Les arguments nommés améliorent également la lisibilité de votre code en identifiant ce que chaque argument représente.</span><span class="sxs-lookup"><span data-stu-id="96602-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="96602-116">Dans l’exemple de méthode ci-dessous, `sellerName` ne peut pas être une valeur Null ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="96602-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="96602-117">`sellerName` et `productName` étant tous deux des types de chaînes, au lieu d’envoyer les arguments par position, il est plus logique d’utiliser des arguments nommés pour lever l’ambiguïté entre les deux et réduire les risques de confusion pour toute personne lisant le code.</span><span class="sxs-lookup"><span data-stu-id="96602-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="96602-118">Les arguments nommés, quand ils sont utilisés avec des arguments de position, sont valides tant que :</span><span class="sxs-lookup"><span data-stu-id="96602-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="96602-119">Ils ne sont pas suivis d’arguments de position, ou</span><span class="sxs-lookup"><span data-stu-id="96602-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="96602-120">_À compter de C# 7.2_ , ils sont utilisés dans la position correcte</span><span class="sxs-lookup"><span data-stu-id="96602-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="96602-121">Dans l’exemple ci-dessous, le paramètre `orderNum` est à la position correcte, mais il n’est pas explicitement nommé.</span><span class="sxs-lookup"><span data-stu-id="96602-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="96602-122">Toutefois, les arguments nommés qui ne sont pas dans l’ordre ne sont pas valides s’ils sont suivis d’arguments de position.</span><span class="sxs-lookup"><span data-stu-id="96602-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="96602-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="96602-123">Example</span></span>  
 <span data-ttu-id="96602-124">Le code suivant implémente les exemples de cette section, ainsi que d’autres exemples.</span><span class="sxs-lookup"><span data-stu-id="96602-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="96602-125">Arguments facultatifs</span><span class="sxs-lookup"><span data-stu-id="96602-125">Optional Arguments</span></span>  
 <span data-ttu-id="96602-126">La définition d’une méthode, d’un constructeur, d’un indexeur ou d’un délégué peut spécifier que ses paramètres sont obligatoires ou facultatifs.</span><span class="sxs-lookup"><span data-stu-id="96602-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="96602-127">Chaque appel doit fournir des arguments pour tous les paramètres obligatoires, mais peut omettre les arguments des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="96602-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="96602-128">Dans sa définition, chaque paramètre facultatif a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="96602-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="96602-129">Si aucun argument n’est envoyé pour ce paramètre, la valeur par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="96602-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="96602-130">Une valeur par défaut doit être l’un des types d’expressions suivants :</span><span class="sxs-lookup"><span data-stu-id="96602-130">A default value must be one of the following types of expressions:</span></span>  
  
- <span data-ttu-id="96602-131">une expression constante ;</span><span class="sxs-lookup"><span data-stu-id="96602-131">a constant expression;</span></span>  
  
- <span data-ttu-id="96602-132">une expression de la forme `new ValType()`, où `ValType` est un type valeur (par exemple, [enum](../../../csharp/language-reference/keywords/enum.md) ou [struct](../../../csharp/programming-guide/classes-and-structs/structs.md)) ;</span><span class="sxs-lookup"><span data-stu-id="96602-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
- <span data-ttu-id="96602-133">une expression de la forme [default(ValType)](../../../csharp/language-reference/operators/default.md), où `ValType` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="96602-133">an expression of the form [default(ValType)](../../../csharp/language-reference/operators/default.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="96602-134">Les paramètres facultatifs sont définis à la fin de la liste de paramètres, après tous les paramètres obligatoires.</span><span class="sxs-lookup"><span data-stu-id="96602-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="96602-135">Si l’appelant fournit un argument pour l’un des paramètres d’une série de paramètres facultatifs, il doit fournir des arguments pour tous les paramètres facultatifs précédents.</span><span class="sxs-lookup"><span data-stu-id="96602-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="96602-136">Les intervalles séparés par des virgules ne sont pas autorisés dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="96602-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="96602-137">Par exemple, dans le code suivant, la méthode d’instance `ExampleMethod` est définie avec un paramètre obligatoire et deux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="96602-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="96602-138">L’appel suivant à `ExampleMethod` provoque une erreur du compilateur, car un argument est fourni pour le troisième paramètre, mais pas pour le deuxième.</span><span class="sxs-lookup"><span data-stu-id="96602-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="96602-139">Toutefois, si vous connaissez le nom du troisième paramètre, vous pouvez utiliser un argument nommé pour effectuer la tâche.</span><span class="sxs-lookup"><span data-stu-id="96602-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="96602-140">IntelliSense indique les paramètres facultatifs par des crochets, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="96602-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>  
  
 ![Capture d’écran montrant l’info express IntelliSense pour la méthode ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
>  <span data-ttu-id="96602-142">Vous pouvez aussi déclarer des paramètres facultatifs à l’aide de la classe <xref:System.Runtime.InteropServices.OptionalAttribute> .NET.</span><span class="sxs-lookup"><span data-stu-id="96602-142">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="96602-143">Les paramètres `OptionalAttribute` ne nécessitent pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="96602-143">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96602-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="96602-144">Example</span></span>  
 <span data-ttu-id="96602-145">Dans l’exemple suivant, le constructeur associé à `ExampleClass` a un seul paramètre, qui est facultatif.</span><span class="sxs-lookup"><span data-stu-id="96602-145">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="96602-146">La méthode d’instance `ExampleMethod` a un paramètre obligatoire (`required`) et deux paramètres facultatifs (`optionalstr` et `optionalint`).</span><span class="sxs-lookup"><span data-stu-id="96602-146">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="96602-147">Le code dans `Main` montre les différentes façons dont le constructeur et la méthode peuvent être appelés.</span><span class="sxs-lookup"><span data-stu-id="96602-147">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="96602-148">Interfaces COM</span><span class="sxs-lookup"><span data-stu-id="96602-148">COM Interfaces</span></span>  
 <span data-ttu-id="96602-149">Avec la prise en charge des objets dynamiques et d’autres améliorations, les arguments nommés et facultatifs améliorent nettement l’interopérabilité avec les API COM, telles que les API Office Automation.</span><span class="sxs-lookup"><span data-stu-id="96602-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="96602-150">Par exemple, la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> de l’interface <xref:Microsoft.Office.Interop.Excel.Range> de Microsoft Office Excel comporte sept paramètres, tous facultatifs.</span><span class="sxs-lookup"><span data-stu-id="96602-150">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="96602-151">Ces paramètres sont indiqués dans l’illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="96602-151">These parameters are shown in the following illustration:</span></span>  
  
 ![Capture d’écran montrant l’info express IntelliSense pour la méthode AutoFormat.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 <span data-ttu-id="96602-153">Dans C# 3.0 et les versions antérieures, un argument est obligatoire pour chaque paramètre, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="96602-153">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="96602-154">Toutefois, vous pouvez considérablement simplifier l’appel à `AutoFormat` en utilisant les arguments nommés et facultatifs introduits dans C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="96602-154">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="96602-155">Les paramètres nommés et facultatifs vous permettent d’omettre l’argument d’un paramètre obligatoire si vous ne souhaitez pas modifier la valeur par défaut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="96602-155">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="96602-156">Dans l’appel suivant, une valeur est spécifiée pour un seul des sept paramètres.</span><span class="sxs-lookup"><span data-stu-id="96602-156">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="96602-157">Pour obtenir plus d’informations et d’exemples, consultez [Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) et [Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="96602-157">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="96602-158">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="96602-158">Overload Resolution</span></span>  
 <span data-ttu-id="96602-159">L’utilisation d’arguments nommés et facultatifs affecte la résolution de surcharge des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="96602-159">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
- <span data-ttu-id="96602-160">Une méthode, un indexeur ou un constructeur est un candidat pour l’exécution si chacun de ses paramètres est facultatif ou correspond, par son nom ou sa position, à un seul argument dans l’instruction appelante, et que cet argument peut être converti vers le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="96602-160">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
- <span data-ttu-id="96602-161">Si plusieurs candidats sont trouvés, les règles de résolution de surcharge des conversions préférées sont appliquées aux arguments qui sont explicitement spécifiés.</span><span class="sxs-lookup"><span data-stu-id="96602-161">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="96602-162">Les arguments omis pour les paramètres facultatifs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="96602-162">Omitted arguments for optional parameters are ignored.</span></span>  
  
- <span data-ttu-id="96602-163">Si deux candidats sont jugés de qualité équivalente, la préférence va à celui qui n’a pas de paramètres facultatifs pour lesquels des arguments ont été omis dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="96602-163">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="96602-164">Ceci s’explique par l’application d’une préférence générale dans la résolution de surcharge en faveur des candidats qui ont le moins de paramètres.</span><span class="sxs-lookup"><span data-stu-id="96602-164">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="96602-165">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="96602-165">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="96602-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96602-166">See also</span></span>

- [<span data-ttu-id="96602-167">Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office</span><span class="sxs-lookup"><span data-stu-id="96602-167">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="96602-168">Utilisation du type dynamic</span><span class="sxs-lookup"><span data-stu-id="96602-168">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="96602-169">Utilisation de constructeurs</span><span class="sxs-lookup"><span data-stu-id="96602-169">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [<span data-ttu-id="96602-170">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="96602-170">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)
