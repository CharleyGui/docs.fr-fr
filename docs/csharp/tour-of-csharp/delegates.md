---
title: Délégués C# - Visite guidée du langage C#
description: Découvrez la liaison tardive avec les délégués C#
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159167"
---
# <a name="delegates"></a><span data-ttu-id="baa36-103">Délégués</span><span class="sxs-lookup"><span data-stu-id="baa36-103">Delegates</span></span>

<span data-ttu-id="baa36-104">Un ***type délégué*** représente des références à des méthodes avec une liste de paramètres et un type de retour particuliers.</span><span class="sxs-lookup"><span data-stu-id="baa36-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="baa36-105">Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres.</span><span class="sxs-lookup"><span data-stu-id="baa36-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="baa36-106">Les délégués sont similaires au concept de pointeurs de fonction trouvés dans d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="baa36-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="baa36-107">Contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="baa36-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="baa36-108">L’exemple suivant déclare et utilise un type délégué nommé `Function`.</span><span class="sxs-lookup"><span data-stu-id="baa36-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="baa36-109">Une instance du type délégué `Function` peut faire référence à toute méthode qui accepte un argument `double` et retourne une valeur `double`.</span><span class="sxs-lookup"><span data-stu-id="baa36-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="baa36-110">La méthode `Apply` applique une fonction donnée aux éléments d’un `double[]`, et retourne un `double[]` avec les résultats.</span><span class="sxs-lookup"><span data-stu-id="baa36-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="baa36-111">Dans la méthode `Main`, `Apply` sert à appliquer trois fonctions différentes à un `double[]`.</span><span class="sxs-lookup"><span data-stu-id="baa36-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="baa36-112">Un délégué peut faire référence à une méthode statique (comme `Square` ou `Math.Sin` dans l’exemple précédent) ou à une méthode d’instance (comme `m.Multiply` dans l’exemple précédent).</span><span class="sxs-lookup"><span data-stu-id="baa36-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="baa36-113">Un délégué qui référence une méthode d’instance référence aussi un objet particulier, et quand la méthode d’instance est appelée via le délégué, cet objet devient `this` dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="baa36-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="baa36-114">Les délégués peuvent également être créés à l’aide de fonctions anonymes, qui sont des « méthodes inline » qui sont créées lorsqu’elles sont déclarées.</span><span class="sxs-lookup"><span data-stu-id="baa36-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="baa36-115">Les fonctions anonymes peuvent voir les variables locales des méthodes qui l’entourent.</span><span class="sxs-lookup"><span data-stu-id="baa36-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="baa36-116">L’exemple suivant ne crée pas de classe :</span><span class="sxs-lookup"><span data-stu-id="baa36-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="baa36-117">Un délégué ne connaît pas ou ne tient pas compte de la classe de la méthode qu’il référence ; Il est important que la méthode référencée ait les mêmes paramètres et le même type de retour que le délégué.</span><span class="sxs-lookup"><span data-stu-id="baa36-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="baa36-118">[Précédent](interfaces.md)
>[Suivant](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="baa36-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
