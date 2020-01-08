---
title: Délégués C# - Visite guidée du langage C#
description: Découvrez la liaison tardive avec les délégués C#
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 317d3ee6fb1350824fa9b3b4d0e3e851780ce4d4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346877"
---
# <a name="delegates"></a><span data-ttu-id="741d5-103">Délégués</span><span class="sxs-lookup"><span data-stu-id="741d5-103">Delegates</span></span>

<span data-ttu-id="741d5-104">Un ***type délégué*** représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers.</span><span class="sxs-lookup"><span data-stu-id="741d5-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="741d5-105">Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres.</span><span class="sxs-lookup"><span data-stu-id="741d5-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="741d5-106">Les délégués sont similaires au concept de pointeurs de fonction dans d’autres langages, mais contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="741d5-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="741d5-107">L’exemple suivant déclare et utilise un type délégué nommé `Function`.</span><span class="sxs-lookup"><span data-stu-id="741d5-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="741d5-108">Une instance du type délégué `Function` peut faire référence à toute méthode qui accepte un argument `double` et retourne une valeur `double`.</span><span class="sxs-lookup"><span data-stu-id="741d5-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="741d5-109">La méthode `Apply` applique une fonction donnée aux éléments d’un `double[]`, et retourne un `double[]` avec les résultats.</span><span class="sxs-lookup"><span data-stu-id="741d5-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="741d5-110">Dans la méthode `Main`, `Apply` sert à appliquer trois fonctions différentes à un `double[]`.</span><span class="sxs-lookup"><span data-stu-id="741d5-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="741d5-111">Un délégué peut faire référence à une méthode statique (comme `Square` ou `Math.Sin` dans l’exemple précédent) ou à une méthode d’instance (comme `m.Multiply` dans l’exemple précédent).</span><span class="sxs-lookup"><span data-stu-id="741d5-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="741d5-112">Un délégué qui référence une méthode d’instance référence aussi un objet particulier, et quand la méthode d’instance est appelée via le délégué, cet objet devient `this` dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="741d5-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="741d5-113">Les délégués peuvent également être créés à l’aide de fonctions anonymes, qui sont des « méthodes inline » créées à la volée.</span><span class="sxs-lookup"><span data-stu-id="741d5-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="741d5-114">Les fonctions anonymes peuvent voir les variables locales des méthodes qui l’entourent.</span><span class="sxs-lookup"><span data-stu-id="741d5-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="741d5-115">Par conséquent, l’exemple de multiplicateur ci-dessus peut être écrit plus facilement sans utiliser une classe Multiplicateur :</span><span class="sxs-lookup"><span data-stu-id="741d5-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="741d5-116">Une propriété intéressante et utile d’un délégué est qu’il ne connaît pas la classe de la méthode qu’il référence, et cela lui est égal. Tout ce qui importe est que la méthode référencée ait les mêmes paramètres et type de retour que le délégué.</span><span class="sxs-lookup"><span data-stu-id="741d5-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="741d5-117">[Précédent](interfaces.md)
>[Suivant](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="741d5-117">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
