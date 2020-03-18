---
title: Comment mettre en œuvre les accesseurs d’événements personnalisés - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705351"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="df1c6-102">Comment mettre en œuvre des accesseurs d’événements personnalisés (Guide de programmation CMD)</span><span class="sxs-lookup"><span data-stu-id="df1c6-102">How to implement custom event accessors (C# Programming Guide)</span></span>
<span data-ttu-id="df1c6-103">Un événement constitue un genre spécial de délégué multicast qui peut être appelé uniquement à partir de la classe dans laquelle il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="df1c6-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="df1c6-104">Le code client s’abonne à l’événement en fournissant une référence à une méthode qui doit être appelée quand l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="df1c6-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="df1c6-105">Ces méthodes sont ajoutées à la liste d’invocation du délégué par le biais des accesseurs d’événement, qui ressemblent aux accesseurs de propriété, sauf que les accesseurs d’événement sont nommés `add` et `remove`.</span><span class="sxs-lookup"><span data-stu-id="df1c6-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="df1c6-106">Dans la plupart des cas, vous n’avez pas à fournir d’accesseurs d’événement personnalisés.</span><span class="sxs-lookup"><span data-stu-id="df1c6-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="df1c6-107">Quand aucun accesseur d’événement personnalisé n’est fourni dans votre code, le compilateur les ajoute automatiquement.</span><span class="sxs-lookup"><span data-stu-id="df1c6-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="df1c6-108">Toutefois, vous devez parfois fournir un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="df1c6-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="df1c6-109">Un tel cas est montré dans le sujet [Comment implémenter des événements d’interface](./how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="df1c6-109">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="df1c6-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="df1c6-110">Example</span></span>  
 <span data-ttu-id="df1c6-111">L’exemple suivant indique comment implémenter des accesseurs d’événement add et remove.</span><span class="sxs-lookup"><span data-stu-id="df1c6-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="df1c6-112">Même si vous pouvez remplacer le code à l’intérieur des accesseurs, nous vous recommandons de verrouiller l’événement avant d’ajouter ou de supprimer une nouvelle méthode de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="df1c6-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="df1c6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df1c6-113">See also</span></span>

- [<span data-ttu-id="df1c6-114">Événements</span><span class="sxs-lookup"><span data-stu-id="df1c6-114">Events</span></span>](./index.md)
- [<span data-ttu-id="df1c6-115">Événement</span><span class="sxs-lookup"><span data-stu-id="df1c6-115">event</span></span>](../../language-reference/keywords/event.md)
