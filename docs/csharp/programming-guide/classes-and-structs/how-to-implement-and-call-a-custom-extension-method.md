---
title: Comment mettre en œuvre et appeler une méthode d’extension personnalisée - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7e2092a37c1f042a087e03f4a272139b585156c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705598"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="e0bfe-102">Comment mettre en œuvre et appeler une méthode d’extension personnalisée (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="e0bfe-102">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="e0bfe-103">Cette rubrique montre comment implémenter vos propres méthodes d’extension pour n’importe quel type .NET.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="e0bfe-104">Le code client peut utiliser vos méthodes d’extension en ajoutant une référence à la DLL qui les contient, et en ajoutant une directive [using](../../language-reference/keywords/using-directive.md) qui spécifie l’espace de noms dans lequel les méthodes d’extension sont définies.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="e0bfe-105">Pour définir et appeler la méthode d’extension</span><span class="sxs-lookup"><span data-stu-id="e0bfe-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="e0bfe-106">Définissez une classe statiquepour contenir la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="e0bfe-107">La classe doit être visible par le code client.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-107">The class must be visible to client code.</span></span> <span data-ttu-id="e0bfe-108">Pour plus d’informations sur les règles d’accessibilité, consultez [Modificateurs d’accès](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="e0bfe-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="e0bfe-109">Implémentez la méthode d’extension en tant que méthode statique avec au moins la même visibilité que la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="e0bfe-110">Le premier paramètre de la méthode spécifie le type sur lequel la méthode opère. Il doit être précédé du modificateur [this](../../language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="e0bfe-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="e0bfe-111">Dans le code appelant, ajoutez une directive `using` pour spécifier l’[espace de noms](../../language-reference/keywords/namespace.md) qui contient la classe de méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="e0bfe-112">Appelez les méthodes comme s’il s’agissait de méthodes d’instance sur le type.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="e0bfe-113">Notez que le premier paramètre n’est pas spécifié par le code appelant, car il représente le type sur lequel l’opérateur est appliqué, et le compilateur connaît déjà le type de votre objet.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="e0bfe-114">Vous devez fournir des arguments uniquement pour les paramètres 2 à `n`.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0bfe-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e0bfe-115">Example</span></span>  
 <span data-ttu-id="e0bfe-116">L’exemple suivant implémente une méthode d’extension nommée `WordCount` dans la classe `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="e0bfe-117">La méthode opère sur la classe <xref:System.String>, qui est spécifiée comme premier paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="e0bfe-118">L’espace de noms `CustomExtensions` est importé dans l’espace de noms d’application, et la méthode est appelée à l’intérieur de la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="e0bfe-119">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e0bfe-119">.NET Framework Security</span></span>  
 <span data-ttu-id="e0bfe-120">Les méthodes d’extension ne présentent aucune faille de sécurité spécifique.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="e0bfe-121">Elles ne peuvent jamais être utilisées pour emprunter l’identité des méthodes existantes sur un type, car toutes les collisions de noms sont résolues en faveur de l’instance ou de la méthode statique définie par le type lui-même.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="e0bfe-122">Les méthodes d’extension ne peuvent pas accéder à des données privées dans la classe étendue.</span><span class="sxs-lookup"><span data-stu-id="e0bfe-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bfe-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0bfe-123">See also</span></span>

- [<span data-ttu-id="e0bfe-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e0bfe-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e0bfe-125">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="e0bfe-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="e0bfe-126">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="e0bfe-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="e0bfe-127">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="e0bfe-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="e0bfe-128">Protégé</span><span class="sxs-lookup"><span data-stu-id="e0bfe-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="e0bfe-129">Interne</span><span class="sxs-lookup"><span data-stu-id="e0bfe-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="e0bfe-130">public</span><span class="sxs-lookup"><span data-stu-id="e0bfe-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="e0bfe-131">Ce</span><span class="sxs-lookup"><span data-stu-id="e0bfe-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="e0bfe-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="e0bfe-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
