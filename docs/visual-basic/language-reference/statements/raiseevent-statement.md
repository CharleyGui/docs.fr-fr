---
title: RaiseEvent, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: 46b93c060a12d82b34dafdf3aa4ea677df6f54cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404289"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="4028b-102">RaiseEvent, instruction</span><span class="sxs-lookup"><span data-stu-id="4028b-102">RaiseEvent Statement</span></span>
<span data-ttu-id="4028b-103">Déclenche un événement déclaré au niveau du module au sein d’une classe, d’un formulaire ou d’un document.</span><span class="sxs-lookup"><span data-stu-id="4028b-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4028b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4028b-104">Syntax</span></span>  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="4028b-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="4028b-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="4028b-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4028b-106">Required.</span></span> <span data-ttu-id="4028b-107">Nom de l’événement à déclencher.</span><span class="sxs-lookup"><span data-stu-id="4028b-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="4028b-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4028b-108">Optional.</span></span> <span data-ttu-id="4028b-109">Liste de variables, de tableaux ou d’expressions délimitée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4028b-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="4028b-110">L' `argumentlist` argument doit être placé entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="4028b-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="4028b-111">S’il n’y a pas d’arguments, les parenthèses doivent être omises.</span><span class="sxs-lookup"><span data-stu-id="4028b-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4028b-112">Notes</span><span class="sxs-lookup"><span data-stu-id="4028b-112">Remarks</span></span>  
 <span data-ttu-id="4028b-113">Le requis `eventname` est le nom d’un événement déclaré dans le module.</span><span class="sxs-lookup"><span data-stu-id="4028b-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="4028b-114">Il suit Visual Basic conventions d’affectation des noms de variables.</span><span class="sxs-lookup"><span data-stu-id="4028b-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="4028b-115">Si l’événement n’a pas été déclaré dans le module dans lequel il est déclenché, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="4028b-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="4028b-116">Le fragment de code suivant illustre une déclaration d’événement et une procédure dans laquelle l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="4028b-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="4028b-117">Vous ne pouvez pas utiliser `RaiseEvent` pour déclencher des événements qui ne sont pas explicitement déclarés dans le module.</span><span class="sxs-lookup"><span data-stu-id="4028b-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="4028b-118">Par exemple, tous les formulaires héritent d’un <xref:System.Windows.Forms.Control.Click> événement de <xref:System.Windows.Forms.Form?displayProperty=nameWithType> , il ne peut pas être déclenché à l’aide `RaiseEvent` de dans un formulaire dérivé.</span><span class="sxs-lookup"><span data-stu-id="4028b-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="4028b-119">Si vous déclarez un `Click` événement dans le module de formulaire, il occulte le propre événement du formulaire <xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="4028b-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="4028b-120">Vous pouvez toujours appeler l’événement du formulaire <xref:System.Windows.Forms.Control.Click> en appelant la <xref:System.Windows.Forms.Control.OnClick%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="4028b-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="4028b-121">Par défaut, un événement défini dans Visual Basic déclenche ses gestionnaires d’événements dans l’ordre dans lequel les connexions sont établies.</span><span class="sxs-lookup"><span data-stu-id="4028b-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="4028b-122">Étant donné que les événements peuvent avoir des `ByRef` paramètres, un processus qui se connecte tardivement peut recevoir des paramètres qui ont été modifiés par un gestionnaire d’événements antérieur.</span><span class="sxs-lookup"><span data-stu-id="4028b-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="4028b-123">Une fois que les gestionnaires d’événements s’exécutent, le contrôle est retourné à la sous-routine qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="4028b-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4028b-124">Les événements non partagés ne doivent pas être déclenchés dans le constructeur de la classe dans laquelle ils sont déclarés.</span><span class="sxs-lookup"><span data-stu-id="4028b-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="4028b-125">Bien que ces événements ne provoquent pas d’erreurs d’exécution, ils peuvent ne pas être détectés par les gestionnaires d’événements associés.</span><span class="sxs-lookup"><span data-stu-id="4028b-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="4028b-126">Utilisez le `Shared` modificateur pour créer un événement partagé si vous devez déclencher un événement à partir d’un constructeur.</span><span class="sxs-lookup"><span data-stu-id="4028b-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4028b-127">Vous pouvez modifier le comportement par défaut des événements en définissant un événement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4028b-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="4028b-128">Pour les événements personnalisés, l' `RaiseEvent` instruction appelle l’accesseur de l’événement `RaiseEvent` .</span><span class="sxs-lookup"><span data-stu-id="4028b-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="4028b-129">Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4028b-129">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4028b-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="4028b-130">Example</span></span>  
 <span data-ttu-id="4028b-131">L'exemple suivant utilise des événements pour décompter les secondes de 10 à 0.</span><span class="sxs-lookup"><span data-stu-id="4028b-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="4028b-132">Le code illustre plusieurs méthodes, propriétés et instructions liées aux événements, y compris l' `RaiseEvent` instruction.</span><span class="sxs-lookup"><span data-stu-id="4028b-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="4028b-133">La classe qui déclenche un événement est la source de l'événement, et les méthodes qui traitent l'événement sont les gestionnaires d'événements.</span><span class="sxs-lookup"><span data-stu-id="4028b-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="4028b-134">Une source d'événement peut avoir plusieurs gestionnaires pour les événements qu'elle génère.</span><span class="sxs-lookup"><span data-stu-id="4028b-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="4028b-135">Quand la classe déclenche l'événement, celui-ci se produit pour chaque classe ayant choisi de gérer les événements pour cette instance de l'objet.</span><span class="sxs-lookup"><span data-stu-id="4028b-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="4028b-136">L'exemple utilise également un formulaire (`Form1`) avec un bouton (`Button1`) et une zone de texte (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="4028b-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="4028b-137">Quand vous cliquez sur le bouton, la première zone de texte affiche un compte à rebours de 10 à 0 secondes.</span><span class="sxs-lookup"><span data-stu-id="4028b-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="4028b-138">Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».</span><span class="sxs-lookup"><span data-stu-id="4028b-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="4028b-139">Le code correspondant à `Form1` indique les états de début et de fin du formulaire.</span><span class="sxs-lookup"><span data-stu-id="4028b-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="4028b-140">Il contient également le code exécuté lors du déclenchement des événements.</span><span class="sxs-lookup"><span data-stu-id="4028b-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="4028b-141">Pour utiliser cet exemple, ouvrez un nouveau projet d’application Windows, ajoutez un bouton nommé `Button1` et une zone de texte nommée `TextBox1` au formulaire principal, nommé `Form1` .</span><span class="sxs-lookup"><span data-stu-id="4028b-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="4028b-142">Cliquez ensuite avec le bouton droit sur le formulaire, puis cliquez sur **afficher le code** pour ouvrir l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="4028b-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="4028b-143">Ajoutez une `WithEvents` variable à la section declarations de la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="4028b-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="4028b-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="4028b-144">Example</span></span>  
 <span data-ttu-id="4028b-145">Ajoutez le code suivant au code pour `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4028b-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="4028b-146">Remplacez toutes les procédures en double qui peuvent exister, telles que `Form_Load` , ou `Button_Click` .</span><span class="sxs-lookup"><span data-stu-id="4028b-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="4028b-147">Appuyez sur F5 pour exécuter l’exemple précédent, puis cliquez sur le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="4028b-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="4028b-148">La première zone de texte commence à décompter les secondes.</span><span class="sxs-lookup"><span data-stu-id="4028b-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="4028b-149">Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».</span><span class="sxs-lookup"><span data-stu-id="4028b-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4028b-150">La `My.Application.DoEvents` méthode ne traite pas les événements exactement de la même façon que le formulaire.</span><span class="sxs-lookup"><span data-stu-id="4028b-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="4028b-151">Pour permettre au formulaire de gérer directement les événements, vous pouvez utiliser le multithreading.</span><span class="sxs-lookup"><span data-stu-id="4028b-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="4028b-152">Pour plus d’informations, consultez [threads managés](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="4028b-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4028b-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4028b-153">See also</span></span>

- [<span data-ttu-id="4028b-154">Événements</span><span class="sxs-lookup"><span data-stu-id="4028b-154">Events</span></span>](../../programming-guide/language-features/events/index.md)
- [<span data-ttu-id="4028b-155">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="4028b-155">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="4028b-156">AddHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="4028b-156">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="4028b-157">RemoveHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="4028b-157">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="4028b-158">Poignées</span><span class="sxs-lookup"><span data-stu-id="4028b-158">Handles</span></span>](handles-clause.md)
