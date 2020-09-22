---
title: Le modificateur 'Custom' n'est pas valide pour les événements déclarés sans types délégués explicites
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 88cdeccd7a3411b57a77116bde64d0a2cf8e537d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874539"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="a5005-102">Le modificateur 'Custom' n'est pas valide pour les événements déclarés sans types délégués explicites</span><span class="sxs-lookup"><span data-stu-id="a5005-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>

<span data-ttu-id="a5005-103">Contrairement à un événement non personnalisé, une `Custom Event` déclaration requiert une `As` clause qui suit le nom de l’événement qui spécifie explicitement le type délégué de l’événement.</span><span class="sxs-lookup"><span data-stu-id="a5005-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="a5005-104">Les événements non personnalisés peuvent être définis à l’aide d’une `As` clause et d’un type délégué explicite, ou avec une liste de paramètres qui suit immédiatement le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="a5005-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="a5005-105">**ID d’erreur :** BC31122</span><span class="sxs-lookup"><span data-stu-id="a5005-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a5005-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a5005-106">To correct this error</span></span>  
  
1. <span data-ttu-id="a5005-107">Définissez un délégué avec la même liste de paramètres que l’événement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a5005-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="a5005-108">Par exemple, si le `Custom Event` a été défini par `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , le délégué correspondant est le suivant.</span><span class="sxs-lookup"><span data-stu-id="a5005-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. <span data-ttu-id="a5005-109">Remplacez la liste de paramètres de l’événement personnalisé par une `As` clause qui spécifie le type délégué.</span><span class="sxs-lookup"><span data-stu-id="a5005-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="a5005-110">Pour continuer avec l’exemple, la `Custom Event` déclaration est réécrite comme suit.</span><span class="sxs-lookup"><span data-stu-id="a5005-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="a5005-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5005-111">Example</span></span>  

 <span data-ttu-id="a5005-112">Cet exemple déclare un `Custom Event` et spécifie la `As` clause requise avec un type délégué.</span><span class="sxs-lookup"><span data-stu-id="a5005-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a5005-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5005-113">See also</span></span>

- [<span data-ttu-id="a5005-114">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="a5005-114">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="a5005-115">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="a5005-115">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="a5005-116">Événements</span><span class="sxs-lookup"><span data-stu-id="a5005-116">Events</span></span>](../../programming-guide/language-features/events/index.md)
