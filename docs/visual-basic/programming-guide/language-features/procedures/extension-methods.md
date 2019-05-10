---
title: Méthodes d'extension (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 48a2609a1931e55d24d98cd2b336fc16c520c948
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649639"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="f39c4-102">Méthodes d'extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f39c4-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="f39c4-103">Méthodes d’extension permettent aux développeurs d’ajouter des fonctionnalités personnalisées aux types de données qui sont déjà définis sans créer un nouveau type dérivé.</span><span class="sxs-lookup"><span data-stu-id="f39c4-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="f39c4-104">Méthodes d’extension permettent d’écrire une méthode qui peut être appelée comme s’il s’agissait d’une méthode d’instance du type existant.</span><span class="sxs-lookup"><span data-stu-id="f39c4-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f39c4-105">Notes</span><span class="sxs-lookup"><span data-stu-id="f39c4-105">Remarks</span></span>  
 <span data-ttu-id="f39c4-106">Une méthode d’extension peut uniquement être un `Sub` procédure ou un `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="f39c4-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="f39c4-107">Vous ne pouvez pas définir une propriété d’extension, un champ ou un événement.</span><span class="sxs-lookup"><span data-stu-id="f39c4-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="f39c4-108">Toutes les méthodes d’extension doivent être marqués avec l’attribut d’extension `<Extension()>` à partir de la <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f39c4-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="f39c4-109">Le premier paramètre dans une définition de méthode d’extension Spécifie le type de données que la méthode étend.</span><span class="sxs-lookup"><span data-stu-id="f39c4-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="f39c4-110">Lorsque la méthode est exécutée, le premier paramètre est lié à l’instance du type de données qui appelle la méthode.</span><span class="sxs-lookup"><span data-stu-id="f39c4-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f39c4-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="f39c4-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f39c4-112">Description</span><span class="sxs-lookup"><span data-stu-id="f39c4-112">Description</span></span>  
 <span data-ttu-id="f39c4-113">L’exemple suivant définit un `Print` extension pour le <xref:System.String> type de données.</span><span class="sxs-lookup"><span data-stu-id="f39c4-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="f39c4-114">Utilise la méthode `Console.WriteLine` pour afficher une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f39c4-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="f39c4-115">Le paramètre de la `Print` (méthode), `aString`, indique que la méthode étend la <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="f39c4-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]  
  
 <span data-ttu-id="f39c4-116">Notez que la définition de méthode d’extension est marquée avec l’attribut d’extension `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="f39c4-116">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="f39c4-117">Le marquage du module dans lequel la méthode est définie est facultatif, mais chaque méthode d’extension doit être marqué.</span><span class="sxs-lookup"><span data-stu-id="f39c4-117">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="f39c4-118"><xref:System.Runtime.CompilerServices> doit être importé afin d’accéder à l’attribut d’extension.</span><span class="sxs-lookup"><span data-stu-id="f39c4-118"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="f39c4-119">Méthodes d’extension peuvent être déclarées que dans les modules.</span><span class="sxs-lookup"><span data-stu-id="f39c4-119">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="f39c4-120">En règle générale, le module dans lequel une méthode d’extension est définie n’est pas le même module que celui dans lequel elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="f39c4-120">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="f39c4-121">Au lieu de cela, le module qui contient la méthode d’extension est importé, s’il a besoin être placé dans la portée.</span><span class="sxs-lookup"><span data-stu-id="f39c4-121">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="f39c4-122">Une fois le module qui contient `Print` est dans la portée, la méthode peut être appelée comme s’il s’agissait d’une méthode d’instance ordinaire qui n’accepte aucun argument, tel que `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="f39c4-122">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]  
  
 <span data-ttu-id="f39c4-123">L’exemple suivant, `PrintAndPunctuate`, est également une extension à <xref:System.String>, cette fois définie avec deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="f39c4-123">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="f39c4-124">Le premier paramètre, `aString`, indique que la méthode d’extension étend <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f39c4-124">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="f39c4-125">Le deuxième paramètre, `punc`, est destinée à être une chaîne de signes de ponctuation qui est passée comme un argument lorsque la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="f39c4-125">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="f39c4-126">La méthode affiche la chaîne suivie de la ponctuation.</span><span class="sxs-lookup"><span data-stu-id="f39c4-126">The method displays the string followed by the punctuation marks.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]  
  
 <span data-ttu-id="f39c4-127">La méthode est appelée en envoyant un argument de chaîne pour `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="f39c4-127">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="f39c4-128">L’exemple suivant `Print` et `PrintAndPunctuate` définies et appelées.</span><span class="sxs-lookup"><span data-stu-id="f39c4-128">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="f39c4-129"><xref:System.Runtime.CompilerServices> est importé dans le module de définition afin d’activer l’accès à l’attribut d’extension.</span><span class="sxs-lookup"><span data-stu-id="f39c4-129"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f39c4-130">Code</span><span class="sxs-lookup"><span data-stu-id="f39c4-130">Code</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="f39c4-131">Ensuite, les méthodes d’extension sont placées dans la portée et appelées.</span><span class="sxs-lookup"><span data-stu-id="f39c4-131">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="f39c4-132">Commentaires</span><span class="sxs-lookup"><span data-stu-id="f39c4-132">Comments</span></span>  
 <span data-ttu-id="f39c4-133">Tout ce qui est nécessaire pour être en mesure d’exécuter ces commandes ou des méthodes d’extension similaire est qu’elles dans la portée.</span><span class="sxs-lookup"><span data-stu-id="f39c4-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="f39c4-134">Si le module qui contient une méthode d’extension est dans la portée, il est visible dans IntelliSense et peut être appelée comme s’il s’agissait d’une méthode d’instance ordinaire.</span><span class="sxs-lookup"><span data-stu-id="f39c4-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="f39c4-135">Notez que lorsque les méthodes sont appelées, aucun argument n’est envoyé pour le premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="f39c4-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="f39c4-136">Paramètre `aString` dans la méthode précédente définitions est lié à `example`, l’instance de `String` qui les appelle.</span><span class="sxs-lookup"><span data-stu-id="f39c4-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="f39c4-137">Le compilateur utilisera `example` comme argument envoyé au premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="f39c4-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="f39c4-138">Si une méthode d’extension est appelée pour un objet qui a la valeur `Nothing`, la méthode d’extension s’exécute.</span><span class="sxs-lookup"><span data-stu-id="f39c4-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="f39c4-139">Cela ne s’applique pas aux méthodes d’instance ordinaire.</span><span class="sxs-lookup"><span data-stu-id="f39c4-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="f39c4-140">Vous pouvez explicitement vérifier `Nothing` dans la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="f39c4-140">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="f39c4-141">Types qui peuvent être étendus</span><span class="sxs-lookup"><span data-stu-id="f39c4-141">Types That Can Be Extended</span></span>  
 <span data-ttu-id="f39c4-142">Vous pouvez définir une méthode d’extension sur la plupart des types qui peuvent être représentés dans une liste de paramètres Visual Basic, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f39c4-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
- <span data-ttu-id="f39c4-143">Classes (types référence)</span><span class="sxs-lookup"><span data-stu-id="f39c4-143">Classes (reference types)</span></span>  
  
- <span data-ttu-id="f39c4-144">Structures (types valeur)</span><span class="sxs-lookup"><span data-stu-id="f39c4-144">Structures (value types)</span></span>  
  
- <span data-ttu-id="f39c4-145">Interfaces</span><span class="sxs-lookup"><span data-stu-id="f39c4-145">Interfaces</span></span>  
  
- <span data-ttu-id="f39c4-146">Délégués</span><span class="sxs-lookup"><span data-stu-id="f39c4-146">Delegates</span></span>  
  
- <span data-ttu-id="f39c4-147">Arguments ByRef et ByVal</span><span class="sxs-lookup"><span data-stu-id="f39c4-147">ByRef and ByVal arguments</span></span>  
  
- <span data-ttu-id="f39c4-148">Paramètres de méthode générique</span><span class="sxs-lookup"><span data-stu-id="f39c4-148">Generic method parameters</span></span>  
  
- <span data-ttu-id="f39c4-149">Tableaux</span><span class="sxs-lookup"><span data-stu-id="f39c4-149">Arrays</span></span>  
  
 <span data-ttu-id="f39c4-150">Étant donné que le premier paramètre spécifie le type de données qui s’étend de la méthode d’extension, il est obligatoire et ne peut pas être facultatif.</span><span class="sxs-lookup"><span data-stu-id="f39c4-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="f39c4-151">Pour cette raison, `Optional` paramètres et `ParamArray` ne peuvent pas être le premier paramètre dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f39c4-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="f39c4-152">Méthodes d’extension ne sont pas considérés comme dans la liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="f39c4-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="f39c4-153">Dans l’exemple suivant, l’instruction `anObject.PrintMe()` déclenche un <xref:System.MissingMemberException> exception, la même exception qu’elle apparaîtrait si la seconde `PrintMe` définition de méthode d’extension ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="f39c4-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]  
  
## <a name="best-practices"></a><span data-ttu-id="f39c4-154">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="f39c4-154">Best Practices</span></span>  
 <span data-ttu-id="f39c4-155">Méthodes d’extension fournissent un moyen pratique et puissant d’étendre un type existant.</span><span class="sxs-lookup"><span data-stu-id="f39c4-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="f39c4-156">Toutefois, pour les utiliser avec succès, il existe quelques points à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="f39c4-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="f39c4-157">Ces considérations s’appliquent principalement aux auteurs de bibliothèques de classes, mais elles peuvent affecter n’importe quelle application qui utilise des méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="f39c4-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="f39c4-158">La plupart du temps, les méthodes d’extension que vous ajoutez aux types que vous ne possédez pas sont plus vulnérables que les méthodes d’extension ajoutées aux types que vous contrôlez.</span><span class="sxs-lookup"><span data-stu-id="f39c4-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="f39c4-159">Un certain nombre de choses peut se produire dans les classes que vous n’êtes pas propriétaire et qui peuvent interférer avec vos méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="f39c4-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
- <span data-ttu-id="f39c4-160">Si n’importe quel membre d’instance accessible existe avec une signature qui est compatible avec les arguments dans l’instruction d’appel, sans conversions restrictives requises d’un argument au paramètre, la méthode d’instance servira préférence à toute méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="f39c4-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="f39c4-161">Par conséquent, si une méthode d’instance appropriée est ajoutée à une classe à un moment donné, un membre d’extension existant que vous dépendez peut devenir inaccessible.</span><span class="sxs-lookup"><span data-stu-id="f39c4-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
- <span data-ttu-id="f39c4-162">L’auteur d’une méthode d’extension ne peut pas empêcher d’autres programmeurs d’écrire des méthodes d’extension en conflit qui peuvent être prioritaires sur l’extension d’origine.</span><span class="sxs-lookup"><span data-stu-id="f39c4-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
- <span data-ttu-id="f39c4-163">Vous pouvez améliorer la robustesse en plaçant les méthodes d’extension dans leur propre espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f39c4-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="f39c4-164">Consommateurs de votre bibliothèque peuvent ensuite inclure un espace de noms exclure ou sélection parmi les espaces de noms, séparément du reste de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f39c4-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
- <span data-ttu-id="f39c4-165">Il peut être plus sûr d’étendre les interfaces plutôt que d’étendre les classes, surtout si vous ne possédez pas l’interface ou la classe.</span><span class="sxs-lookup"><span data-stu-id="f39c4-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="f39c4-166">Une modification dans une interface affecte chaque classe qui l’implémente.</span><span class="sxs-lookup"><span data-stu-id="f39c4-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="f39c4-167">Par conséquent, l’auteur peut être moins tenté d’ajouter ou modifier les méthodes dans une interface.</span><span class="sxs-lookup"><span data-stu-id="f39c4-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="f39c4-168">Toutefois, si une classe implémente deux interfaces qui ont des méthodes d’extension avec la même signature, aucune méthode d’extension est visible.</span><span class="sxs-lookup"><span data-stu-id="f39c4-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
- <span data-ttu-id="f39c4-169">Étendre le type plus spécifique, que vous pouvez.</span><span class="sxs-lookup"><span data-stu-id="f39c4-169">Extend the most specific type you can.</span></span> <span data-ttu-id="f39c4-170">Dans une hiérarchie de types, si vous sélectionnez un type à partir de laquelle d’autres types sont dérivés, il existe des couches de l’introduction de méthodes d’instance ou d’autres méthodes d’extension peuvent interférer avec les vôtres.</span><span class="sxs-lookup"><span data-stu-id="f39c4-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="f39c4-171">Méthodes d’extension, les propriétés et les méthodes d’Instance</span><span class="sxs-lookup"><span data-stu-id="f39c4-171">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="f39c4-172">Lorsqu’une méthode d’instance dans la portée a une signature qui est compatible avec les arguments d’une instruction appelante, la méthode d’instance est choisie dans la préférence n’importe quelle méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="f39c4-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="f39c4-173">La méthode d’instance est prioritaire même si la méthode d’extension est une meilleure correspondance.</span><span class="sxs-lookup"><span data-stu-id="f39c4-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="f39c4-174">Dans l’exemple suivant, `ExampleClass` contient une méthode d’instance nommée `ExampleMethod` qui a un paramètre de type `Integer`.</span><span class="sxs-lookup"><span data-stu-id="f39c4-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="f39c4-175">Méthode d’extension `ExampleMethod` étend `ExampleClass`, et a un paramètre de type `Long`.</span><span class="sxs-lookup"><span data-stu-id="f39c4-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]  
  
 <span data-ttu-id="f39c4-176">Le premier appel à `ExampleMethod` dans le code suivant appelle la méthode d’extension, car `arg1` est `Long` et est compatible uniquement avec le `Long` paramètre dans la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="f39c4-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="f39c4-177">Le deuxième appel à `ExampleMethod` a un `Integer` argument, `arg2`, et il appelle la méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="f39c4-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]  
  
 <span data-ttu-id="f39c4-178">Maintenant inversez les types de données des paramètres dans les deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="f39c4-178">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]  
  
 <span data-ttu-id="f39c4-179">Cette fois, le code dans `Main` appelle la méthode d’instance les deux fois.</span><span class="sxs-lookup"><span data-stu-id="f39c4-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="f39c4-180">Il s’agit, car les deux `arg1` et `arg2` avoir une conversion étendue vers `Long`, et la méthode d’instance est prioritaire sur la méthode d’extension dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="f39c4-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]  
  
 <span data-ttu-id="f39c4-181">Par conséquent, une méthode d’extension ne peut pas remplacer une méthode d’instance existante.</span><span class="sxs-lookup"><span data-stu-id="f39c4-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="f39c4-182">Toutefois, lorsqu’une méthode d’extension a le même nom qu’une méthode d’instance, mais les signatures d’éviter les conflits, les deux méthodes sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="f39c4-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="f39c4-183">Par exemple, si classe `ExampleClass` contient une méthode nommée `ExampleMethod` qui n’accepte aucun arguments, méthodes d’extension portant le même nom mais des signatures différentes sont autorisées, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f39c4-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]  
  
 <span data-ttu-id="f39c4-184">La sortie de ce code est comme suit :</span><span class="sxs-lookup"><span data-stu-id="f39c4-184">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="f39c4-185">La situation est plus simple avec des propriétés : si une méthode d’extension a le même nom en tant que propriété de la classe qu’elle étend, la méthode d’extension n’est pas visible et n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="f39c4-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="f39c4-186">Priorité de méthode d’extension</span><span class="sxs-lookup"><span data-stu-id="f39c4-186">Extension Method Precedence</span></span>  
 <span data-ttu-id="f39c4-187">Deux méthodes d’extension qui ont des signatures identiques sont dans la portée et accessibles, celui avec une priorité plus élevée est appelé.</span><span class="sxs-lookup"><span data-stu-id="f39c4-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="f39c4-188">Priorité d’une méthode d’extension est basée sur le mécanisme utilisé pour placer la méthode dans la portée.</span><span class="sxs-lookup"><span data-stu-id="f39c4-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="f39c4-189">La liste suivante montre la hiérarchie des priorités, du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="f39c4-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1. <span data-ttu-id="f39c4-190">Méthodes d’extension définies dans le module actuel.</span><span class="sxs-lookup"><span data-stu-id="f39c4-190">Extension methods defined inside the current module.</span></span>  
  
2. <span data-ttu-id="f39c4-191">Méthodes d’extension définies à l’intérieur des données de types dans l’espace de noms actuel ou l’un de ses parents, avec des espaces de noms enfants étant prioritaires sur les espaces de noms parent.</span><span class="sxs-lookup"><span data-stu-id="f39c4-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3. <span data-ttu-id="f39c4-192">Méthodes d’extension définies dans les importations de type dans le fichier actuel.</span><span class="sxs-lookup"><span data-stu-id="f39c4-192">Extension methods defined inside any type imports in the current file.</span></span>  
  
4. <span data-ttu-id="f39c4-193">Méthodes d’extension définies dans les importations d’espace de noms dans le fichier actuel.</span><span class="sxs-lookup"><span data-stu-id="f39c4-193">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5. <span data-ttu-id="f39c4-194">Méthodes d’extension définies dans les importations de type au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="f39c4-194">Extension methods defined inside any project-level type imports.</span></span>  
  
6. <span data-ttu-id="f39c4-195">Méthodes d’extension définies dans les importations d’espace de noms au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="f39c4-195">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="f39c4-196">Si la priorité ne résout pas l’ambiguïté, vous pouvez utiliser le nom qualifié complet pour spécifier la méthode que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="f39c4-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="f39c4-197">Si le `Print` méthode dans l’exemple précédent est définie dans un module nommé `StringExtensions`, le nom qualifié complet est `StringExtensions.Print(example)` au lieu de `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="f39c4-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39c4-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f39c4-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="f39c4-199">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="f39c4-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="f39c4-200">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="f39c4-200">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="f39c4-201">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="f39c4-201">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f39c4-202">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="f39c4-202">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="f39c4-203">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="f39c4-203">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="f39c4-204">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="f39c4-204">Attributes overview</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="f39c4-205">Portée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f39c4-205">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
