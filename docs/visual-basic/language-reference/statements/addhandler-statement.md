---
title: AddHandler, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: de995a13b34678410e2af74b59f2d0c467982b75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408482"
---
# <a name="addhandler-statement"></a><span data-ttu-id="a7150-102">AddHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="a7150-102">AddHandler Statement</span></span>
<span data-ttu-id="a7150-103">Associe un événement à un gestionnaire d’événements au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a7150-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7150-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7150-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="a7150-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="a7150-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="a7150-106">event</span><span class="sxs-lookup"><span data-stu-id="a7150-106">event</span></span>|<span data-ttu-id="a7150-107">Nom de l’événement à gérer.</span><span class="sxs-lookup"><span data-stu-id="a7150-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="a7150-108">Nom d’une procédure qui gère l’événement.</span><span class="sxs-lookup"><span data-stu-id="a7150-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="a7150-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a7150-109">Remarks</span></span>  
 <span data-ttu-id="a7150-110">Les `AddHandler` `RemoveHandler` instructions et vous permettent de démarrer et d’arrêter la gestion des événements à tout moment pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="a7150-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="a7150-111">La signature de la `eventhandler` procédure doit correspondre à la signature de l’événement `event` .</span><span class="sxs-lookup"><span data-stu-id="a7150-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="a7150-112">Le mot clé `Handles` et l'instruction `AddHandler` vous permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences.</span><span class="sxs-lookup"><span data-stu-id="a7150-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="a7150-113">L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a7150-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="a7150-114">Utilisez le mot clé `Handles` quand vous définissez une procédure pour indiquer qu'elle gère un événement particulier.</span><span class="sxs-lookup"><span data-stu-id="a7150-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="a7150-115">Pour plus d’informations, consultez [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7150-115">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7150-116">Pour les événements personnalisés, l' `AddHandler` instruction appelle l’accesseur de l’événement `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="a7150-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="a7150-117">Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a7150-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7150-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7150-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="a7150-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7150-119">See also</span></span>

- [<span data-ttu-id="a7150-120">RemoveHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="a7150-120">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="a7150-121">Poignées</span><span class="sxs-lookup"><span data-stu-id="a7150-121">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="a7150-122">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="a7150-122">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="a7150-123">Événements</span><span class="sxs-lookup"><span data-stu-id="a7150-123">Events</span></span>](../../programming-guide/language-features/events/index.md)
