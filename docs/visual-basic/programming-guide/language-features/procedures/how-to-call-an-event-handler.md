---
title: Comment appeler un gestionnaire d’événements
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3762c79dd3d883ae2ccfe76b335cf98ac87d4246
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89464959"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="fe613-102">Comment appeler un gestionnaire d’événements dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe613-102">How to call an event handler in Visual Basic</span></span>

<span data-ttu-id="fe613-103">Un *événement* est une action ou une occurrence, telle qu’un clic de souris ou une limite de crédit dépassée, qui est reconnue par un composant de programme et pour laquelle vous pouvez écrire du code pour répondre.</span><span class="sxs-lookup"><span data-stu-id="fe613-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="fe613-104">Un *Gestionnaire d’événements* est le code que vous écrivez pour répondre à un événement.</span><span class="sxs-lookup"><span data-stu-id="fe613-104">An *event handler* is the code you write to respond to an event.</span></span>

<span data-ttu-id="fe613-105">Un gestionnaire d’événements dans Visual Basic est une `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="fe613-105">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="fe613-106">Toutefois, vous ne l’appelez pas normalement de la même façon que les autres `Sub` procédures.</span><span class="sxs-lookup"><span data-stu-id="fe613-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="fe613-107">Au lieu de cela, vous identifiez la procédure en tant que gestionnaire de l’événement.</span><span class="sxs-lookup"><span data-stu-id="fe613-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="fe613-108">Vous pouvez le faire soit avec une [`Handles`](../../../language-reference/statements/handles-clause.md) clause et une [`WithEvents`](../../../language-reference/modifiers/withevents.md) variable, soit avec une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe613-108">You can do this either with a [`Handles`](../../../language-reference/statements/handles-clause.md) clause and a [`WithEvents`](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="fe613-109">L’utilisation d’une `Handles` clause est la manière par défaut de déclarer un gestionnaire d’événements dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fe613-109">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="fe613-110">C’est la façon dont les gestionnaires d’événements sont écrits par les concepteurs lorsque vous programmez dans l’environnement de développement intégré (IDE).</span><span class="sxs-lookup"><span data-stu-id="fe613-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="fe613-111">L' `AddHandler` instruction est appropriée pour déclencher des événements de manière dynamique au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fe613-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

<span data-ttu-id="fe613-112">Lorsque l’événement se produit, Visual Basic appelle automatiquement la procédure du gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="fe613-112">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="fe613-113">Tout code qui a accès à l’événement peut le faire en exécutant une [instruction RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe613-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

<span data-ttu-id="fe613-114">Vous pouvez associer plusieurs gestionnaires d’événements à un même événement.</span><span class="sxs-lookup"><span data-stu-id="fe613-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="fe613-115">Dans certains cas, vous pouvez dissocier un gestionnaire d’un événement.</span><span class="sxs-lookup"><span data-stu-id="fe613-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="fe613-116">Pour plus d’informations, consultez [Événements](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="fe613-116">For more information, see [Events](../events/index.md).</span></span>

## <a name="call-an-event-handler-using-no-loc-texthandles-and-no-locwithevents"></a><span data-ttu-id="fe613-117">Appeler un gestionnaire d’événements à l’aide :::no-loc text="Handles"::: de et WithEvents</span><span class="sxs-lookup"><span data-stu-id="fe613-117">Call an event handler using :::no-loc text="Handles"::: and WithEvents</span></span>

1. <span data-ttu-id="fe613-118">Assurez-vous que l’événement est déclaré avec une [instruction Event](../../../language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe613-118">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="fe613-119">Déclarez une variable objet au niveau du module ou de la classe, à l’aide du [`WithEvents`](../../../language-reference/modifiers/withevents.md) mot clé.</span><span class="sxs-lookup"><span data-stu-id="fe613-119">Declare an object variable at module or class level, using the [`WithEvents`](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="fe613-120">La `As` clause de cette variable doit spécifier la classe qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="fe613-120">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="fe613-121">Dans la déclaration de la procédure de gestion des événements `Sub` , ajoutez une [`Handles`](../../../language-reference/statements/handles-clause.md) clause qui spécifie la `WithEvents` variable et le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="fe613-121">In the declaration of the event-handling `Sub` procedure, add a [`Handles`](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="fe613-122">Lorsque l’événement se produit, Visual Basic appelle automatiquement la `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="fe613-122">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="fe613-123">Votre code peut utiliser une `RaiseEvent` instruction pour faire en sorte que l’événement se produise.</span><span class="sxs-lookup"><span data-stu-id="fe613-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="fe613-124">L’exemple suivant définit un événement et une `WithEvents` variable qui fait référence à la classe qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="fe613-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="fe613-125">La procédure de gestion des événements `Sub` utilise une `Handles` clause pour spécifier la classe et l’événement qu’elle gère.</span><span class="sxs-lookup"><span data-stu-id="fe613-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a><span data-ttu-id="fe613-126">Appeler un gestionnaire d’événements à l’aide de AddHandler</span><span class="sxs-lookup"><span data-stu-id="fe613-126">Call an event handler using AddHandler</span></span>

1. <span data-ttu-id="fe613-127">Assurez-vous que l’événement est déclaré avec une `Event` instruction.</span><span class="sxs-lookup"><span data-stu-id="fe613-127">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="fe613-128">Exécutez une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) pour connecter dynamiquement la procédure de gestion des événements `Sub` avec l’événement.</span><span class="sxs-lookup"><span data-stu-id="fe613-128">Execute an [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="fe613-129">Lorsque l’événement se produit, Visual Basic appelle automatiquement la `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="fe613-129">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="fe613-130">Votre code peut utiliser une `RaiseEvent` instruction pour faire en sorte que l’événement se produise.</span><span class="sxs-lookup"><span data-stu-id="fe613-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="fe613-131">L’exemple suivant utilise l' [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) dans le constructeur pour associer la `OnFormClosing` procédure en tant que gestionnaire d’événements pour <xref:System.Windows.Forms.Form.FormClosing> .</span><span class="sxs-lookup"><span data-stu-id="fe613-131">The following example uses the [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) in the constructor to associate the `OnFormClosing` procedure as an event handler for <xref:System.Windows.Forms.Form.FormClosing>.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    <span data-ttu-id="fe613-132">Vous pouvez dissocier un gestionnaire d’événements d’un événement en exécutant l' [instruction RemoveHandler](../../../language-reference/statements/removehandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe613-132">You can dissociate an event handler from an event by executing the [RemoveHandler statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe613-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe613-133">See also</span></span>

- [<span data-ttu-id="fe613-134">Procédures</span><span class="sxs-lookup"><span data-stu-id="fe613-134">Procedures</span></span>](index.md)
- [<span data-ttu-id="fe613-135">Sub, procédures</span><span class="sxs-lookup"><span data-stu-id="fe613-135">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="fe613-136">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="fe613-136">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="fe613-137">AddressOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="fe613-137">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="fe613-138">Guide pratique : créer une procédure</span><span class="sxs-lookup"><span data-stu-id="fe613-138">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="fe613-139">Comment : appeler une procédure qui ne retourne pas de valeur</span><span class="sxs-lookup"><span data-stu-id="fe613-139">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)
