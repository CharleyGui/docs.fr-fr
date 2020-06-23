---
title: 'Procédure : simuler des événements de souris et de clavier dans le code'
description: Découvrez comment utiliser les options Windows Forms permet de simuler par programmation les entrées de souris et de clavier.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
ms.openlocfilehash: 9b453787f7fa7f5041f75e04d65557a0a3838bee
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904362"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a><span data-ttu-id="75f8c-103">Procédure : simuler des événements de souris et de clavier dans le code</span><span class="sxs-lookup"><span data-stu-id="75f8c-103">How to: Simulate Mouse and Keyboard Events in Code</span></span>

<span data-ttu-id="75f8c-104">Windows Forms fournit plusieurs options pour simuler par programmation l'entrée de souris et de clavier.</span><span class="sxs-lookup"><span data-stu-id="75f8c-104">Windows Forms provides several options for programmatically simulating mouse and keyboard input.</span></span> <span data-ttu-id="75f8c-105">Cette rubrique offre une vue d'ensemble de ces options.</span><span class="sxs-lookup"><span data-stu-id="75f8c-105">This topic provides an overview of these options.</span></span>

## <a name="simulating-mouse-input"></a><span data-ttu-id="75f8c-106">Simulation de l'entrée de souris</span><span class="sxs-lookup"><span data-stu-id="75f8c-106">Simulating Mouse Input</span></span>

<span data-ttu-id="75f8c-107">Le meilleur moyen de simuler des événements de souris consiste à appeler la méthode `On`*EventName* qui déclenche l'événement de souris que vous souhaitez simuler.</span><span class="sxs-lookup"><span data-stu-id="75f8c-107">The best way to simulate mouse events is to call the `On`*EventName* method that raises the mouse event you want to simulate.</span></span> <span data-ttu-id="75f8c-108">Cette option est généralement possible uniquement dans les contrôles et les formulaires personnalisés, car les méthodes qui déclenchent des événements sont protégées et ne sont pas accessibles en dehors du contrôle ou du formulaire.</span><span class="sxs-lookup"><span data-stu-id="75f8c-108">This option is usually possible only within custom controls and forms, because the methods that raise events are protected and cannot be accessed outside the control or form.</span></span> <span data-ttu-id="75f8c-109">Par exemple, les étapes suivantes illustrent comment simuler un clic sur le bouton droit de la souris dans le code.</span><span class="sxs-lookup"><span data-stu-id="75f8c-109">For example, the following steps illustrate how to simulate clicking the right mouse button in code.</span></span>

#### <a name="to-programmatically-click-the-right-mouse-button"></a><span data-ttu-id="75f8c-110">Pour cliquer sur le bouton droit de la souris par programmation</span><span class="sxs-lookup"><span data-stu-id="75f8c-110">To programmatically click the right mouse button</span></span>

1. <span data-ttu-id="75f8c-111">Créez un <xref:System.Windows.Forms.MouseEventArgs> dont la propriété <xref:System.Windows.Forms.MouseEventArgs.Button%2A> a la valeur <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="75f8c-111">Create a <xref:System.Windows.Forms.MouseEventArgs> whose <xref:System.Windows.Forms.MouseEventArgs.Button%2A> property is set to the <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> value.</span></span>

2. <span data-ttu-id="75f8c-112">Appelez la méthode <xref:System.Windows.Forms.Control.OnMouseClick%2A> avec ce <xref:System.Windows.Forms.MouseEventArgs> comme argument.</span><span class="sxs-lookup"><span data-stu-id="75f8c-112">Call the <xref:System.Windows.Forms.Control.OnMouseClick%2A> method with this <xref:System.Windows.Forms.MouseEventArgs> as the argument.</span></span>

<span data-ttu-id="75f8c-113">Pour plus d’informations sur les contrôles personnalisés, consultez [Développement de contrôles Windows Forms au moment du design](./controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="75f8c-113">For more information on custom controls, see [Developing Windows Forms Controls at Design Time](./controls/developing-windows-forms-controls-at-design-time.md).</span></span>

<span data-ttu-id="75f8c-114">Il existe d'autres manières de simuler l'entrée de souris.</span><span class="sxs-lookup"><span data-stu-id="75f8c-114">There are other ways to simulate mouse input.</span></span> <span data-ttu-id="75f8c-115">Par exemple, vous pouvez définir par programmation une propriété de contrôle qui représente un état qui est généralement défini par une entrée de souris (telle que la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> du contrôle <xref:System.Windows.Forms.CheckBox> ) ou vous pouvez appeler directement le délégué qui est attaché à l'événement que vous souhaitez simuler.</span><span class="sxs-lookup"><span data-stu-id="75f8c-115">For example, you can programmatically set a control property that represents a state that is typically set through mouse input (such as the <xref:System.Windows.Forms.CheckBox.Checked%2A> property of the <xref:System.Windows.Forms.CheckBox> control), or you can directly call the delegate that is attached to the event you want to simulate.</span></span>

## <a name="simulating-keyboard-input"></a><span data-ttu-id="75f8c-116">Simulation de l'entrée au clavier</span><span class="sxs-lookup"><span data-stu-id="75f8c-116">Simulating Keyboard Input</span></span>

<span data-ttu-id="75f8c-117">Bien que vous puissiez simuler l'entrée au clavier à l'aide des stratégies abordées ci-dessus pour l'entrée de souris, Windows Forms fournit également la classe <xref:System.Windows.Forms.SendKeys> pour envoyer des séquences de touches à l'application active.</span><span class="sxs-lookup"><span data-stu-id="75f8c-117">Although you can simulate keyboard input by using the strategies discussed above for mouse input, Windows Forms also provides the <xref:System.Windows.Forms.SendKeys> class for sending keystrokes to the active application.</span></span>

> [!CAUTION]
> <span data-ttu-id="75f8c-118">Si votre application est prévue pour une utilisation internationale avec différents claviers, l'utilisation de <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> peut produire des résultats imprévisibles et doit être évitée.</span><span class="sxs-lookup"><span data-stu-id="75f8c-118">If your application is intended for international use with a variety of keyboards, the use of <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> could yield unpredictable results and should be avoided.</span></span>

> [!NOTE]
> <span data-ttu-id="75f8c-119">La classe <xref:System.Windows.Forms.SendKeys> a été mise à jour pour .NET Framework 3.0 pour pouvoir être utilisée dans les applications qui s'exécutent sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="75f8c-119">The <xref:System.Windows.Forms.SendKeys> class has been updated for the .NET Framework 3.0 to enable its use in applications that run on Windows Vista.</span></span> <span data-ttu-id="75f8c-120">La sécurité renforcée de Windows Vista (également appelée Contrôle de compte d'utilisateur) empêche le fonctionnement correcte de l'implémentation précédente.</span><span class="sxs-lookup"><span data-stu-id="75f8c-120">The enhanced security of Windows Vista (known as User Account Control or UAC) prevents the previous implementation from working as expected.</span></span>
>
> <span data-ttu-id="75f8c-121">La classe <xref:System.Windows.Forms.SendKeys> est vulnérable aux problèmes de synchronisation, que certains développeurs ont dû contourner.</span><span class="sxs-lookup"><span data-stu-id="75f8c-121">The <xref:System.Windows.Forms.SendKeys> class is susceptible to timing issues, which some developers have had to work around.</span></span> <span data-ttu-id="75f8c-122">L'implémentation mise à jour est toujours vulnérable aux problèmes de synchronisation, mais est légèrement plus rapide et peut nécessiter certaines modifications des solutions de contournement.</span><span class="sxs-lookup"><span data-stu-id="75f8c-122">The updated implementation is still susceptible to timing issues, but is slightly faster and may require changes to the workarounds.</span></span> <span data-ttu-id="75f8c-123">La classe <xref:System.Windows.Forms.SendKeys> tente d'abord d'utiliser l'implémentation précédente et, en cas d'échec, utilise la nouvelle implémentation.</span><span class="sxs-lookup"><span data-stu-id="75f8c-123">The <xref:System.Windows.Forms.SendKeys> class tries to use the previous implementation first, and if that fails, uses the new implementation.</span></span> <span data-ttu-id="75f8c-124">Ainsi, la classe <xref:System.Windows.Forms.SendKeys> peut se comporter différemment sur différents systèmes d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="75f8c-124">As a result, the <xref:System.Windows.Forms.SendKeys> class may behave differently on different operating systems.</span></span> <span data-ttu-id="75f8c-125">En outre, quand la classe <xref:System.Windows.Forms.SendKeys> utilise la nouvelle implémentation, la méthode <xref:System.Windows.Forms.SendKeys.SendWait%2A> n'attend pas que les messages soient traités quand ils sont envoyés à un autre processus.</span><span class="sxs-lookup"><span data-stu-id="75f8c-125">Additionally, when the <xref:System.Windows.Forms.SendKeys> class uses the new implementation, the <xref:System.Windows.Forms.SendKeys.SendWait%2A> method will not wait for messages to be processed when they are sent to another process.</span></span>
>
> <span data-ttu-id="75f8c-126">Si votre application repose sur un comportement cohérent indépendamment du système d'exploitation, vous pouvez forcer la classe <xref:System.Windows.Forms.SendKeys> à utiliser la nouvelle implémentation en ajoutant le paramètre d'application suivant à votre fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="75f8c-126">If your application relies on consistent behavior regardless of the operating system, you can force the <xref:System.Windows.Forms.SendKeys> class to use the new implementation by adding the following application setting to your app.config file.</span></span>
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> <span data-ttu-id="75f8c-127">Pour forcer la classe <xref:System.Windows.Forms.SendKeys> à utiliser l'implémentation précédente, utilisez plutôt la valeur `"JournalHook"` .</span><span class="sxs-lookup"><span data-stu-id="75f8c-127">To force the <xref:System.Windows.Forms.SendKeys> class to use the previous implementation, use the value `"JournalHook"` instead.</span></span>

#### <a name="to-send-a-keystroke-to-the-same-application"></a><span data-ttu-id="75f8c-128">Pour envoyer une séquence de touches à la même application</span><span class="sxs-lookup"><span data-stu-id="75f8c-128">To send a keystroke to the same application</span></span>

1. <span data-ttu-id="75f8c-129">Appelez la méthode <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A> de la classe <xref:System.Windows.Forms.SendKeys> .</span><span class="sxs-lookup"><span data-stu-id="75f8c-129">Call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method of the <xref:System.Windows.Forms.SendKeys> class.</span></span> <span data-ttu-id="75f8c-130">Les séquences de touches spécifiées seront reçues par le contrôle actif de l'application.</span><span class="sxs-lookup"><span data-stu-id="75f8c-130">The specified keystrokes will be received by the active control of the application.</span></span> <span data-ttu-id="75f8c-131">L'exemple de code suivant utilise <xref:System.Windows.Forms.SendKeys.Send%2A> pour simuler une pression sur la touche Entrée quand l'utilisateur double-clique sur la surface du formulaire.</span><span class="sxs-lookup"><span data-stu-id="75f8c-131">The following code example uses <xref:System.Windows.Forms.SendKeys.Send%2A> to simulate pressing the ENTER key when the user double-clicks the surface of the form.</span></span> <span data-ttu-id="75f8c-132">Cet exemple suppose que l'on a un <xref:System.Windows.Forms.Form> avec un seul contrôle <xref:System.Windows.Forms.Button> ayant un index de tabulation de 0.</span><span class="sxs-lookup"><span data-stu-id="75f8c-132">This example assumes a <xref:System.Windows.Forms.Form> with a single <xref:System.Windows.Forms.Button> control that has a tab index of 0.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a><span data-ttu-id="75f8c-133">Pour envoyer une séquence de touches vers une autre application</span><span class="sxs-lookup"><span data-stu-id="75f8c-133">To send a keystroke to a different application</span></span>

1. <span data-ttu-id="75f8c-134">Activez la fenêtre d'application qui recevra les séquences de touches, puis appelez la méthode <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A> .</span><span class="sxs-lookup"><span data-stu-id="75f8c-134">Activate the application window that will receive the keystrokes, and then call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method.</span></span> <span data-ttu-id="75f8c-135">Comme il n'existe aucune méthode managée permettant d'activer une autre application, vous devez utiliser des méthodes Windows natives pour forcer le focus sur d'autres applications.</span><span class="sxs-lookup"><span data-stu-id="75f8c-135">Because there is no managed method to activate another application, you must use native Windows methods to force focus on other applications.</span></span> <span data-ttu-id="75f8c-136">L'exemple de code suivant utilise l'appel de code non managé pour appeler les méthodes `FindWindow` et `SetForegroundWindow` pour activer la fenêtre de l'application Calculatrice, puis appelle <xref:System.Windows.Forms.SendKeys.SendWait%2A> pour émettre une série de calculs vers l'application Calculatrice.</span><span class="sxs-lookup"><span data-stu-id="75f8c-136">The following code example uses platform invoke to call the `FindWindow` and `SetForegroundWindow` methods to activate the Calculator application window, and then calls <xref:System.Windows.Forms.SendKeys.SendWait%2A> to issue a series of calculations to the Calculator application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="75f8c-137">Les paramètres corrects de l'appel `FindWindow` qui recherche l'application Calculatrice varient en fonction de votre version de Windows.</span><span class="sxs-lookup"><span data-stu-id="75f8c-137">The correct parameters of the `FindWindow` call that locates the Calculator application vary based on your version of Windows.</span></span>  <span data-ttu-id="75f8c-138">Le code suivant recherche l’application Calculator sur Windows 7.</span><span class="sxs-lookup"><span data-stu-id="75f8c-138">The following code finds the Calculator application on Windows 7.</span></span> <span data-ttu-id="75f8c-139">Sur Windows Vista, remplacez le premier paramètre par « SciCalc ».</span><span class="sxs-lookup"><span data-stu-id="75f8c-139">On Windows Vista, change the first parameter to "SciCalc".</span></span> <span data-ttu-id="75f8c-140">Vous pouvez utiliser l'outil Spy++, fourni avec Visual Studio, pour déterminer les paramètres corrects.</span><span class="sxs-lookup"><span data-stu-id="75f8c-140">You can use the Spy++ tool, included with Visual Studio, to determine the correct parameters.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a><span data-ttu-id="75f8c-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="75f8c-141">Example</span></span>

<span data-ttu-id="75f8c-142">L'exemple de code suivant est l'application complète pour les exemples de code précédents.</span><span class="sxs-lookup"><span data-stu-id="75f8c-142">The following code example is the complete application for the previous code examples.</span></span>

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="75f8c-143">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="75f8c-143">Compiling the Code</span></span>

<span data-ttu-id="75f8c-144">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="75f8c-144">This example requires:</span></span>

- <span data-ttu-id="75f8c-145">des références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="75f8c-145">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="75f8c-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75f8c-146">See also</span></span>

- [<span data-ttu-id="75f8c-147">Entrées d'utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75f8c-147">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
