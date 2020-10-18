---
title: Le modificateur 'Custom' n'est pas valide pour les événements déclarés sans types délégués explicites
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: a2277e3778c2c252fd4b1eaeb033d549f041c15c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160631"
---
# <a name="bc31122-custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="ecaf9-102">BC31122 : le modificateur’Custom’n’est pas valide pour les événements déclarés sans types délégués explicites</span><span class="sxs-lookup"><span data-stu-id="ecaf9-102">BC31122: 'Custom' modifier is not valid on events declared without explicit delegate types</span></span>

<span data-ttu-id="ecaf9-103">Contrairement à un événement non personnalisé, une `Custom Event` déclaration requiert une `As` clause qui suit le nom de l’événement qui spécifie explicitement le type délégué de l’événement.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>

 <span data-ttu-id="ecaf9-104">Les événements non personnalisés peuvent être définis à l’aide d’une `As` clause et d’un type délégué explicite, ou avec une liste de paramètres qui suit immédiatement le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>

 <span data-ttu-id="ecaf9-105">**ID d’erreur :** BC31122</span><span class="sxs-lookup"><span data-stu-id="ecaf9-105">**Error ID:** BC31122</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ecaf9-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ecaf9-106">To correct this error</span></span>

1. <span data-ttu-id="ecaf9-107">Définissez un délégué avec la même liste de paramètres que l’événement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-107">Define a delegate with the same parameter list as the custom event.</span></span>

     <span data-ttu-id="ecaf9-108">Par exemple, si le `Custom Event` a été défini par `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , le délégué correspondant est le suivant.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>

     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]

2. <span data-ttu-id="ecaf9-109">Remplacez la liste de paramètres de l’événement personnalisé par une `As` clause qui spécifie le type délégué.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>

     <span data-ttu-id="ecaf9-110">Pour continuer avec l’exemple, la `Custom Event` déclaration est réécrite comme suit.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>

     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]

## <a name="example"></a><span data-ttu-id="ecaf9-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ecaf9-111">Example</span></span>

 <span data-ttu-id="ecaf9-112">Cet exemple déclare un `Custom Event` et spécifie la `As` clause requise avec un type délégué.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>

 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]

## <a name="see-also"></a><span data-ttu-id="ecaf9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecaf9-113">See also</span></span>

- [<span data-ttu-id="ecaf9-114">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="ecaf9-114">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="ecaf9-115">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="ecaf9-115">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="ecaf9-116">Événements</span><span class="sxs-lookup"><span data-stu-id="ecaf9-116">Events</span></span>](../../programming-guide/language-features/events/index.md)
