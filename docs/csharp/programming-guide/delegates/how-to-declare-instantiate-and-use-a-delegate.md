---
title: Comment déclarer, instantanément et utiliser un délégué - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712362"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="880ac-102">Comment déclarer, instantanément et utiliser un délégué (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="880ac-102">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="880ac-103">Dans C# 1.0 et versions ultérieures, vous pouvez déclarer des délégués comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="880ac-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="880ac-104">C# 2.0 offre un moyen plus simple d’écrire la déclaration précédente, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="880ac-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="880ac-105">Dans C# 2.0 et versions ultérieures, vous pouvez aussi utiliser une méthode anonyme pour déclarer et initialiser un [délégué](../../language-reference/builtin-types/reference-types.md), comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="880ac-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="880ac-106">Dans C# 3.0 et versions ultérieures, vous pouvez aussi déclarer et instancier des délégués à l’aide d’une expression lambda, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="880ac-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="880ac-107">Pour plus d’informations, voir [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="880ac-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="880ac-108">L’exemple suivant illustre la déclaration, l’instanciation et l’utilisation d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="880ac-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="880ac-109">La classe `BookDB` encapsule une base de données de librairie qui tient à jour un inventaire des livres.</span><span class="sxs-lookup"><span data-stu-id="880ac-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="880ac-110">Elle expose une méthode, `ProcessPaperbackBooks`, qui recherche tous les livres de poche dans la base de données et appelle un délégué pour chacun d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="880ac-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="880ac-111">Le type `delegate` qui est utilisé se nomme `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="880ac-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="880ac-112">La classe `Test` utilise cette classe pour imprimer les titres et le prix moyen des livres de poche.</span><span class="sxs-lookup"><span data-stu-id="880ac-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="880ac-113">L’utilisation des délégués favorise une bonne séparation des fonctionnalités entre la base de données de librairie et le code client.</span><span class="sxs-lookup"><span data-stu-id="880ac-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="880ac-114">Le code client n’a aucune connaissance de la façon dont les livres sont stockés, ni de la façon dont le code librairie trouve les livres de poche.</span><span class="sxs-lookup"><span data-stu-id="880ac-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="880ac-115">Le code librairie n’a aucune connaissance du traitement effectué sur les livres de poche une fois qu’il les a trouvés.</span><span class="sxs-lookup"><span data-stu-id="880ac-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="880ac-116"> Exemple</span><span class="sxs-lookup"><span data-stu-id="880ac-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="880ac-117">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="880ac-117">Robust Programming</span></span>  
  
- <span data-ttu-id="880ac-118">Déclaration d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="880ac-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="880ac-119">L’instruction suivante déclare un nouveau type délégué.</span><span class="sxs-lookup"><span data-stu-id="880ac-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="880ac-120">Chaque type délégué décrit le nombre et les types des arguments, ainsi que le type de la valeur de retour des méthodes qu’il peut encapsuler.</span><span class="sxs-lookup"><span data-stu-id="880ac-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="880ac-121">Chaque fois qu’un nouvel ensemble de types d’arguments ou de types de valeur de retour est nécessaire, un nouveau type délégué doit être déclaré.</span><span class="sxs-lookup"><span data-stu-id="880ac-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="880ac-122">Instanciation d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="880ac-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="880ac-123">Une fois que vous avez déclaré un type délégué, vous devez créer un objet délégué et l’associer à une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="880ac-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="880ac-124">Pour cela, dans l’exemple précédent vous passez la méthode `PrintTitle` à la méthode `ProcessPaperbackBooks`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="880ac-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="880ac-125">Cela crée un nouvel objet délégué associé à la méthode [statique](../../language-reference/keywords/static.md)`Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="880ac-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="880ac-126">De même, la méthode non statique `AddBookToTotal` sur l’objet `totaller` est passée comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="880ac-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="880ac-127">Dans les deux cas, un nouvel objet délégué est passé à la méthode `ProcessPaperbackBooks`.</span><span class="sxs-lookup"><span data-stu-id="880ac-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="880ac-128">Une fois un délégué créé, la méthode à laquelle il est associé ne change jamais. Les objets délégué sont immuables.</span><span class="sxs-lookup"><span data-stu-id="880ac-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="880ac-129">Appel d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="880ac-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="880ac-130">Une fois créé, un objet délégué est généralement passé à un autre code qui appellera le délégué.</span><span class="sxs-lookup"><span data-stu-id="880ac-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="880ac-131">Pour appeler un objet délégué, vous devez utiliser le nom de l’objet délégué, suivi des arguments entre parenthèses à passer au délégué.</span><span class="sxs-lookup"><span data-stu-id="880ac-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="880ac-132">Voici un exemple d’appel de délégué :</span><span class="sxs-lookup"><span data-stu-id="880ac-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="880ac-133">Vous pouvez appeler un délégué de manière synchrone, comme dans cet exemple, ou de manière asynchrone à l’aide des méthodes `BeginInvoke` et `EndInvoke`.</span><span class="sxs-lookup"><span data-stu-id="880ac-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880ac-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="880ac-134">See also</span></span>

- [<span data-ttu-id="880ac-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="880ac-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="880ac-136">Événements</span><span class="sxs-lookup"><span data-stu-id="880ac-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="880ac-137">Délégués</span><span class="sxs-lookup"><span data-stu-id="880ac-137">Delegates</span></span>](./index.md)
