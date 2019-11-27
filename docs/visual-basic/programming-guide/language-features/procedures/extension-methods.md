---
title: Méthodes d'extension
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: a88756fce9137f89db1b6b8b007d528e98381830
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341174"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="b6b9a-102">Méthodes d'extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6b9a-102">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="b6b9a-103">Les méthodes d’extension permettent aux développeurs d’ajouter des fonctionnalités personnalisées aux types de données qui sont déjà définis sans créer de type dérivé.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="b6b9a-104">Les méthodes d’extension permettent d’écrire une méthode qui peut être appelée comme s’il s’agissait d’une méthode d’instance du type existant.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6b9a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="b6b9a-105">Remarks</span></span>

<span data-ttu-id="b6b9a-106">Une méthode d’extension peut être uniquement une procédure `Sub` ou une procédure `Function`.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="b6b9a-107">Vous ne pouvez pas définir une propriété, un champ ou un événement d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="b6b9a-108">Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension `<Extension>` à partir de l’espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> et doivent être définies dans un [module](../../../language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6b9a-108">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="b6b9a-109">Si une méthode d’extension est définie à l’extérieur d’un module, le compilateur Visual Basic génère l’erreur [BC36551](../../../misc/bc36551.md), « les méthodes d’extension ne peuvent être définies que dans des modules ».</span><span class="sxs-lookup"><span data-stu-id="b6b9a-109">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="b6b9a-110">Le premier paramètre d’une définition de méthode d’extension spécifie le type de données que la méthode étend.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-110">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="b6b9a-111">Lorsque la méthode est exécutée, le premier paramètre est lié à l’instance du type de données qui appelle la méthode.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-111">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="b6b9a-112">L’attribut `Extension` ne peut être appliqué qu’à un Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md)ou [`Function`](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6b9a-112">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="b6b9a-113">Si vous l’appliquez à un `Class` ou à un `Structure`, le compilateur Visual Basic génère l’erreur [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), l’attribut’extension’ne peut être appliqué qu’aux déclarations’module', 'Sub’ou’Function'.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-113">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="b6b9a-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6b9a-114">Example</span></span>

<span data-ttu-id="b6b9a-115">L’exemple suivant définit une extension de `Print` pour le type de données <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-115">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="b6b9a-116">La méthode utilise `Console.WriteLine` pour afficher une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-116">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="b6b9a-117">Le paramètre de la méthode `Print`, `aString`, établit que la méthode étend la classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-117">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="b6b9a-118">Notez que la définition de la méthode d’extension est marquée avec l’attribut d’extension `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-118">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="b6b9a-119">Le marquage du module dans lequel la méthode est définie est facultatif, mais chaque méthode d’extension doit être marquée.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-119">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="b6b9a-120">les <xref:System.Runtime.CompilerServices> doivent être importés pour accéder à l’attribut d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-120"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="b6b9a-121">Les méthodes d’extension ne peuvent être déclarées que dans des modules.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-121">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="b6b9a-122">En général, le module dans lequel une méthode d’extension est définie n’est pas le même que celui dans lequel il est appelé.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-122">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="b6b9a-123">Au lieu de cela, le module qui contient la méthode d’extension est importé, si nécessaire, pour le placer dans la portée.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-123">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="b6b9a-124">Une fois que le module qui contient `Print` est dans la portée, la méthode peut être appelée comme s’il s’agissait d’une méthode d’instance ordinaire qui ne prend pas d’arguments, comme `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="b6b9a-124">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="b6b9a-125">L’exemple suivant, `PrintAndPunctuate`, est également une extension de <xref:System.String>, cette fois définie avec deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="b6b9a-126">Le premier paramètre, `aString`, établit que la méthode d’extension étend <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="b6b9a-127">Le deuxième paramètre, `punc`, est destiné à être une chaîne de signes de ponctuation qui est passée comme argument lorsque la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="b6b9a-128">La méthode affiche la chaîne suivie des signes de ponctuation.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-128">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="b6b9a-129">La méthode est appelée en envoyant un argument de chaîne pour `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="b6b9a-129">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="b6b9a-130">L’exemple suivant montre `Print` et `PrintAndPunctuate` définis et appelés.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-130">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="b6b9a-131"><xref:System.Runtime.CompilerServices> est importé dans le module de définition afin d’autoriser l’accès à l’attribut d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-131"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="b6b9a-132">Ensuite, les méthodes d’extension sont mises en portée et appelées :</span><span class="sxs-lookup"><span data-stu-id="b6b9a-132">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="b6b9a-133">Tout ce qui est nécessaire pour pouvoir exécuter ces méthodes d’extension ou similaires, c’est qu’elles se trouvent dans la portée.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="b6b9a-134">Si le module qui contient une méthode d’extension est dans la portée, il est visible dans IntelliSense et peut être appelé comme s’il s’agissait d’une méthode d’instance ordinaire.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="b6b9a-135">Notez que lorsque les méthodes sont appelées, aucun argument n’est envoyé dans pour le premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="b6b9a-136">Les `aString` de paramètres dans les définitions de méthode précédentes sont liées à `example`, l’instance de `String` qui les appelle.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="b6b9a-137">Le compilateur utilise `example` comme argument envoyé au premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="b6b9a-138">Si une méthode d’extension est appelée pour un objet qui a la valeur `Nothing`, la méthode d’extension s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="b6b9a-139">Cela ne s’applique pas aux méthodes d’instance ordinaires.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="b6b9a-140">Vous pouvez vérifier explicitement `Nothing` dans la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-140">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="b6b9a-141">Types pouvant être étendus</span><span class="sxs-lookup"><span data-stu-id="b6b9a-141">Types that can be extended</span></span>

<span data-ttu-id="b6b9a-142">Vous pouvez définir une méthode d’extension sur la plupart des types qui peuvent être représentés dans une liste de paramètres Visual Basic, y compris les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b6b9a-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="b6b9a-143">Classes (types référence)</span><span class="sxs-lookup"><span data-stu-id="b6b9a-143">Classes (reference types)</span></span>
- <span data-ttu-id="b6b9a-144">Structures (types valeur)</span><span class="sxs-lookup"><span data-stu-id="b6b9a-144">Structures (value types)</span></span>
- <span data-ttu-id="b6b9a-145">Interfaces</span><span class="sxs-lookup"><span data-stu-id="b6b9a-145">Interfaces</span></span>
- <span data-ttu-id="b6b9a-146">Délégués</span><span class="sxs-lookup"><span data-stu-id="b6b9a-146">Delegates</span></span>
- <span data-ttu-id="b6b9a-147">Arguments ByRef et ByVal</span><span class="sxs-lookup"><span data-stu-id="b6b9a-147">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="b6b9a-148">Paramètres de méthode générique</span><span class="sxs-lookup"><span data-stu-id="b6b9a-148">Generic method parameters</span></span>
- <span data-ttu-id="b6b9a-149">Tableaux</span><span class="sxs-lookup"><span data-stu-id="b6b9a-149">Arrays</span></span>

<span data-ttu-id="b6b9a-150">Étant donné que le premier paramètre spécifie le type de données étendu par la méthode d’extension, il est obligatoire et ne peut pas être facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="b6b9a-151">Pour cette raison, `Optional` paramètres et `ParamArray` paramètres ne peuvent pas être le premier paramètre de la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="b6b9a-152">Les méthodes d’extension ne sont pas prises en compte dans la liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="b6b9a-153">Dans l’exemple suivant, l’instruction `anObject.PrintMe()` lève une exception <xref:System.MissingMemberException>, la même exception que vous pouvez voir si la deuxième définition de la méthode d’extension `PrintMe` a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="b6b9a-154">meilleures pratiques recommandées.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-154">Best practices</span></span>

<span data-ttu-id="b6b9a-155">Les méthodes d’extension offrent un moyen pratique et puissant d’étendre un type existant.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="b6b9a-156">Toutefois, pour les utiliser correctement, il existe des points à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="b6b9a-157">Ces considérations s’appliquent principalement aux auteurs de bibliothèques de classes, mais elles peuvent affecter n’importe quelle application qui utilise des méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="b6b9a-158">En règle générale, les méthodes d’extension que vous ajoutez aux types que vous ne possédez pas sont plus vulnérables que les méthodes d’extension ajoutées aux types que vous contrôlez.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="b6b9a-159">Un certain nombre de choses peuvent se produire dans les classes dont vous n’êtes pas propriétaire et qui peuvent interférer avec vos méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="b6b9a-160">S’il existe un membre d’instance accessible qui a une signature compatible avec les arguments de l’instruction d’appel, sans conversions restrictives requises d’argument en paramètre, la méthode d’instance est utilisée de préférence à toute méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="b6b9a-161">Par conséquent, si une méthode d’instance appropriée est ajoutée à une classe à un moment donné, un membre d’extension existant sur lequel vous vous fiez peut devenir inaccessible.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="b6b9a-162">L’auteur d’une méthode d’extension ne peut pas empêcher d’autres programmeurs d’écrire des méthodes d’extension conflictuelles qui peuvent avoir priorité sur l’extension d’origine.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="b6b9a-163">Vous pouvez améliorer la robustesse en plaçant des méthodes d’extension dans leur propre espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="b6b9a-164">Les consommateurs de votre bibliothèque peuvent alors inclure un espace de noms ou l’exclure, ou sélectionner parmi les espaces de noms, séparément du reste de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="b6b9a-165">Il peut être plus sûr d’étendre les interfaces que d’étendre les classes, en particulier si vous n’êtes pas propriétaire de l’interface ou de la classe.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="b6b9a-166">Une modification dans une interface affecte chaque classe qui l’implémente.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="b6b9a-167">Par conséquent, l’auteur peut être moins susceptible d’ajouter ou de modifier des méthodes dans une interface.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="b6b9a-168">Toutefois, si une classe implémente deux interfaces qui ont des méthodes d’extension avec la même signature, aucune méthode d’extension n’est visible.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="b6b9a-169">Étendez le type le plus spécifique que vous pouvez.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-169">Extend the most specific type you can.</span></span> <span data-ttu-id="b6b9a-170">Dans une hiérarchie de types, si vous sélectionnez un type à partir duquel de nombreux autres types sont dérivés, il existe des couches de possibilités pour l’introduction de méthodes d’instance ou d’autres méthodes d’extension qui peuvent interférer avec les vôtres.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="b6b9a-171">Méthodes d’extension, méthodes d’instance et propriétés</span><span class="sxs-lookup"><span data-stu-id="b6b9a-171">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="b6b9a-172">Quand une méthode d’instance dans la portée a une signature qui est compatible avec les arguments d’une instruction d’appel, la méthode d’instance est choisie de préférence à toute méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="b6b9a-173">La méthode d’instance a la priorité, même si la méthode d’extension est une meilleure correspondance.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="b6b9a-174">Dans l’exemple suivant, `ExampleClass` contient une méthode d’instance nommée `ExampleMethod` qui a un paramètre de type `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="b6b9a-175">La méthode d’extension `ExampleMethod` étend `ExampleClass`et a un paramètre de type `Long`.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="b6b9a-176">Le premier appel à `ExampleMethod` dans le code suivant appelle la méthode d’extension, car `arg1` est `Long` et est compatible uniquement avec le paramètre `Long` dans la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="b6b9a-177">Le deuxième appel à `ExampleMethod` a un argument `Integer`, `arg2`, et il appelle la méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="b6b9a-178">À présent, inversez les types de données des paramètres dans les deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="b6b9a-178">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="b6b9a-179">Cette fois, le code de `Main` appelle la méthode d’instance à la fois.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="b6b9a-180">Cela est dû au fait que `arg1` et `arg2` ont une conversion étendue en `Long`et que la méthode d’instance est prioritaire sur la méthode d’extension dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="b6b9a-181">Par conséquent, une méthode d’extension ne peut pas remplacer une méthode d’instance existante.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="b6b9a-182">Toutefois, lorsqu’une méthode d’extension porte le même nom qu’une méthode d’instance, mais que les signatures ne sont pas en conflit, les deux méthodes sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="b6b9a-183">Par exemple, si la classe `ExampleClass` contient une méthode nommée `ExampleMethod` qui n’accepte aucun argument, les méthodes d’extension portant le même nom mais des signatures différentes sont autorisées, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="b6b9a-184">Le résultat de ce code est le suivant :</span><span class="sxs-lookup"><span data-stu-id="b6b9a-184">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="b6b9a-185">La situation est plus simple avec des propriétés : si une méthode d’extension porte le même nom qu’une propriété de la classe qu’elle étend, la méthode d’extension n’est pas visible et n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="b6b9a-186">Priorité de la méthode d’extension</span><span class="sxs-lookup"><span data-stu-id="b6b9a-186">Extension method precedence</span></span>

<span data-ttu-id="b6b9a-187">Lorsque deux méthodes d’extension qui ont des signatures identiques sont dans la portée et sont accessibles, celle avec une priorité plus élevée est appelée.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="b6b9a-188">La priorité d’une méthode d’extension est basée sur le mécanisme utilisé pour mettre la méthode dans la portée.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="b6b9a-189">La liste suivante affiche la hiérarchie des priorités, du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="b6b9a-190">Méthodes d’extension définies dans le module en cours.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-190">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="b6b9a-191">Méthodes d’extension définies dans les types de données de l’espace de noms actuel ou de l’un de ses parents, les espaces de noms enfants ayant une priorité plus élevée que les espaces de noms parents.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="b6b9a-192">Méthodes d’extension définies dans les importations de type dans le fichier actuel.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-192">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="b6b9a-193">Méthodes d’extension définies dans les importations d’espaces de noms dans le fichier actuel.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-193">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="b6b9a-194">Méthodes d’extension définies dans les importations de type au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-194">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="b6b9a-195">Méthodes d’extension définies dans les importations d’espaces de noms au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-195">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="b6b9a-196">Si la précédence ne résout pas l’ambiguïté, vous pouvez utiliser le nom qualifié complet pour spécifier la méthode que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="b6b9a-197">Si la méthode `Print` dans l’exemple précédent est définie dans un module nommé `StringExtensions`, le nom qualifié complet est `StringExtensions.Print(example)` au lieu de `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="b6b9a-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6b9a-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6b9a-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="b6b9a-199">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="b6b9a-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="b6b9a-200">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="b6b9a-200">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="b6b9a-201">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="b6b9a-201">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b6b9a-202">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="b6b9a-202">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="b6b9a-203">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="b6b9a-203">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="b6b9a-204">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="b6b9a-204">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="b6b9a-205">Étendue dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6b9a-205">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
