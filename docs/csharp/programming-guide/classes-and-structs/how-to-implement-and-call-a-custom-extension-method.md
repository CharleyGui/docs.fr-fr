---
title: Comment implémenter et appeler une méthode d’extension personnalisée (Guide de programmation C#)
description: Découvrez comment implémenter des méthodes d’extension pour n’importe quel type .NET. Le code client peut utiliser vos méthodes en ajoutant une référence à une DLL et en ajoutant une directive using.
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: de4cc423e1823351305a23f331b082aa66add1a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190434"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="3b0a8-104">Comment implémenter et appeler une méthode d’extension personnalisée (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3b0a8-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>

<span data-ttu-id="3b0a8-105">Cette rubrique montre comment implémenter vos propres méthodes d’extension pour n’importe quel type .NET.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="3b0a8-106">Le code client peut utiliser vos méthodes d’extension en ajoutant une référence à la DLL qui les contient, et en ajoutant une directive [using](../../language-reference/keywords/using-directive.md) qui spécifie l’espace de noms dans lequel les méthodes d’extension sont définies.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="3b0a8-107">Pour définir et appeler la méthode d’extension</span><span class="sxs-lookup"><span data-stu-id="3b0a8-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="3b0a8-108">Définissez une classe statiquepour contenir la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="3b0a8-109">La classe doit être visible par le code client.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-109">The class must be visible to client code.</span></span> <span data-ttu-id="3b0a8-110">Pour plus d’informations sur les règles d’accessibilité, consultez [Modificateurs d’accès](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="3b0a8-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="3b0a8-111">Implémentez la méthode d’extension en tant que méthode statique avec au moins la même visibilité que la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="3b0a8-112">Le premier paramètre de la méthode spécifie le type sur lequel la méthode opère. Il doit être précédé du modificateur [this](../../language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="3b0a8-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="3b0a8-113">Dans le code appelant, ajoutez une directive `using` pour spécifier l’[espace de noms](../../language-reference/keywords/namespace.md) qui contient la classe de méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="3b0a8-114">Appelez les méthodes comme s’il s’agissait de méthodes d’instance sur le type.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="3b0a8-115">Notez que le premier paramètre n’est pas spécifié par le code appelant, car il représente le type sur lequel l’opérateur est appliqué, et le compilateur connaît déjà le type de votre objet.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="3b0a8-116">Vous devez fournir des arguments uniquement pour les paramètres 2 à `n`.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b0a8-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b0a8-117">Example</span></span>  

 <span data-ttu-id="3b0a8-118">L’exemple suivant implémente une méthode d’extension nommée `WordCount` dans la classe `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="3b0a8-119">La méthode opère sur la classe <xref:System.String>, qui est spécifiée comme premier paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="3b0a8-120">L’espace de noms `CustomExtensions` est importé dans l’espace de noms d’application, et la méthode est appelée à l’intérieur de la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="3b0a8-121">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="3b0a8-121">.NET Security</span></span>  

 <span data-ttu-id="3b0a8-122">Les méthodes d’extension ne présentent aucune faille de sécurité spécifique.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="3b0a8-123">Elles ne peuvent jamais être utilisées pour emprunter l’identité des méthodes existantes sur un type, car toutes les collisions de noms sont résolues en faveur de l’instance ou de la méthode statique définie par le type lui-même.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="3b0a8-124">Les méthodes d’extension ne peuvent pas accéder à des données privées dans la classe étendue.</span><span class="sxs-lookup"><span data-stu-id="3b0a8-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0a8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b0a8-125">See also</span></span>

- [<span data-ttu-id="3b0a8-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3b0a8-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b0a8-127">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="3b0a8-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="3b0a8-128">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="3b0a8-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="3b0a8-129">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="3b0a8-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="3b0a8-130">protected</span><span class="sxs-lookup"><span data-stu-id="3b0a8-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="3b0a8-131">internal</span><span class="sxs-lookup"><span data-stu-id="3b0a8-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="3b0a8-132">public</span><span class="sxs-lookup"><span data-stu-id="3b0a8-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="3b0a8-133">this</span><span class="sxs-lookup"><span data-stu-id="3b0a8-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="3b0a8-134">namespace</span><span class="sxs-lookup"><span data-stu-id="3b0a8-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
