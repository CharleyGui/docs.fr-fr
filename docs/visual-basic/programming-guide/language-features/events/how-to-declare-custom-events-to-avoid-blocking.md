---
title: 'Comment : déclarer des événements personnalisés pour éviter les blocages'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a9f9529d468a036d81c4e436429cbdb3207efd6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405155"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="ab240-102">Comment : déclarer des événements personnalisés pour éviter les blocages (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab240-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="ab240-103">Dans certains cas, il est important qu’un gestionnaire d’événements ne bloque pas les gestionnaires d’événements suivants.</span><span class="sxs-lookup"><span data-stu-id="ab240-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="ab240-104">Les événements personnalisés permettent à l’événement d’appeler ses gestionnaires d’événements de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ab240-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="ab240-105">Par défaut, le champ de magasin de stockage d’une déclaration d’événement est un délégué multicast qui combine en série tous les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="ab240-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="ab240-106">Cela signifie que si un gestionnaire prend beaucoup de temps pour s’exécuter, il bloque les autres gestionnaires jusqu’à ce qu’il se termine.</span><span class="sxs-lookup"><span data-stu-id="ab240-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="ab240-107">(Les gestionnaires d’événements de comportement correct ne doivent jamais exécuter des opérations longues ou potentiellement bloquantes.)</span><span class="sxs-lookup"><span data-stu-id="ab240-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="ab240-108">Au lieu d’utiliser l’implémentation par défaut des événements fournis par Visual Basic, vous pouvez utiliser un événement personnalisé pour exécuter les gestionnaires d’événements de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ab240-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab240-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab240-109">Example</span></span>  
 <span data-ttu-id="ab240-110">Dans cet exemple, l' `AddHandler` accesseur ajoute le délégué pour chaque gestionnaire de l' `Click` événement à un <xref:System.Collections.ArrayList> stocké dans le `EventHandlerList` champ.</span><span class="sxs-lookup"><span data-stu-id="ab240-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="ab240-111">Lorsque le code déclenche l' `Click` événement, l' `RaiseEvent` accesseur appelle tous les délégués de gestionnaires d’événements de façon asynchrone à l’aide de la <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="ab240-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="ab240-112">Cette méthode appelle chaque gestionnaire sur un thread de travail et retourne immédiatement, de sorte que les gestionnaires ne peuvent pas s’interfacer mutuellement.</span><span class="sxs-lookup"><span data-stu-id="ab240-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="ab240-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab240-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="ab240-114">Événements</span><span class="sxs-lookup"><span data-stu-id="ab240-114">Events</span></span>](index.md)
- [<span data-ttu-id="ab240-115">Comment : déclarer des événements personnalisés pour économiser la mémoire</span><span class="sxs-lookup"><span data-stu-id="ab240-115">How to: Declare Custom Events To Conserve Memory</span></span>](how-to-declare-custom-events-to-conserve-memory.md)
