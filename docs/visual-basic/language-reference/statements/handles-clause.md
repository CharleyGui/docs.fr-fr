---
title: Handles (clause)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 347f521267d4fd954ac359ab25ed5810cfd71d34
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873255"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="d5a4d-102">Handles, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a4d-102">Handles Clause (Visual Basic)</span></span>

<span data-ttu-id="d5a4d-103">Déclare qu'une procédure gère un événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5a4d-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="d5a4d-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="d5a4d-105">Parts</span></span>  

 `proceduredeclaration`  
 <span data-ttu-id="d5a4d-106">Déclaration de procédure `Sub` pour la procédure qui gérera l'événement.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="d5a4d-107">Liste des événements pour `proceduredeclaration` à gérer, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="d5a4d-108">Les événements doivent être déclenchés par la classe de base pour la classe en cours ou par un objet déclaré à l'aide du mot clé `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5a4d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d5a4d-109">Remarks</span></span>  

 <span data-ttu-id="d5a4d-110">Utilisez le mot clé `Handles` à la fin d'une déclaration de procédure pour que celle-ci gère les événements déclenchés par une variable objet déclarée à l'aide du mot clé `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="d5a4d-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="d5a4d-111">Le mot clé `Handles` peut également être utilisé dans une classe dérivée pour gérer des événements à partir d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="d5a4d-112">Le mot clé `Handles` et l'instruction `AddHandler` vous permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="d5a4d-113">Utilisez le mot clé `Handles` quand vous définissez une procédure pour indiquer qu'elle gère un événement particulier.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="d5a4d-114">L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="d5a4d-115">Pour plus d’informations, consultez l' [instruction AddHandler](addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5a4d-115">For more information, see [AddHandler Statement](addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="d5a4d-116">Pour les événements personnalisés, l’application appelle l’accesseur `AddHandler` de l’événement quand elle ajoute la procédure comme gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="d5a4d-117">Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5a4d-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a4d-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5a4d-118">Example</span></span>  

 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="d5a4d-119">L'exemple suivant montre comment une classe dérivée peut utiliser l'instruction `Handles` pour gérer un événement à partir d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="d5a4d-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5a4d-120">Example</span></span>  

 <span data-ttu-id="d5a4d-121">L’exemple suivant contient deux gestionnaires d’événements de bouton pour un projet d' **application WPF** .</span><span class="sxs-lookup"><span data-stu-id="d5a4d-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="d5a4d-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5a4d-122">Example</span></span>  

 <span data-ttu-id="d5a4d-123">L'exemple suivant est équivalent à l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="d5a4d-124">La liste `eventlist` dans la clause `Handles` contient les événements pour les deux boutons.</span><span class="sxs-lookup"><span data-stu-id="d5a4d-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="d5a4d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5a4d-125">See also</span></span>

- [<span data-ttu-id="d5a4d-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="d5a4d-126">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="d5a4d-127">AddHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="d5a4d-127">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="d5a4d-128">RemoveHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="d5a4d-128">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="d5a4d-129">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="d5a4d-129">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="d5a4d-130">RaiseEvent, instruction</span><span class="sxs-lookup"><span data-stu-id="d5a4d-130">RaiseEvent Statement</span></span>](raiseevent-statement.md)
- [<span data-ttu-id="d5a4d-131">Événements</span><span class="sxs-lookup"><span data-stu-id="d5a4d-131">Events</span></span>](../../programming-guide/language-features/events/index.md)
