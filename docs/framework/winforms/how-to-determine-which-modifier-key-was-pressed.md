---
title: 'Procédure : déterminer la touche de modification activée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964313"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="74410-102">Procédure : déterminer la touche de modification activée</span><span class="sxs-lookup"><span data-stu-id="74410-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="74410-103">Lorsque vous créez une application qui accepte les séquences de touches de l’utilisateur, vous pouvez également surveiller les touches de modification telles que les touches Maj, ALT et CTRL.</span><span class="sxs-lookup"><span data-stu-id="74410-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="74410-104">Quand une touche de modification est enfoncée en combinaison avec d’autres touches, ou avec des clics de souris, votre application peut réagir de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="74410-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="74410-105">Par exemple, si la lettre S est enfoncée, cela peut simplement entraîner l’affichage d’un «s» à l’écran, mais si vous appuyez sur les touches CTRL + S, le document actif peut être enregistré.</span><span class="sxs-lookup"><span data-stu-id="74410-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="74410-106">Si vous gérez l' <xref:System.Windows.Forms.Control.KeyDown> événement, la <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> propriété du <xref:System.Windows.Forms.KeyEventArgs> reçu par le gestionnaire d’événements spécifie quelles touches de modification sont enfoncées.</span><span class="sxs-lookup"><span data-stu-id="74410-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="74410-107">La <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> propriété de spécifie également <xref:System.Windows.Forms.KeyEventArgs> le caractère qui a été activé, ainsi que les touches de modification associées à une opération or au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="74410-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="74410-108">Toutefois, si vous gérez l' <xref:System.Windows.Forms.Control.KeyPress> événement ou un événement de souris, le gestionnaire d’événements ne reçoit pas ces informations.</span><span class="sxs-lookup"><span data-stu-id="74410-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="74410-109">Dans ce cas, vous devez utiliser la <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriété de la <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="74410-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="74410-110">Dans les deux cas, vous devez effectuer une opération de bits and <xref:System.Windows.Forms.Keys> de la valeur appropriée et de la valeur que vous testez.</span><span class="sxs-lookup"><span data-stu-id="74410-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="74410-111">L' <xref:System.Windows.Forms.Keys> énumération offre des variations de chaque touche de modification. il est donc important que vous exécutiez l’opération de bits and avec la valeur correcte.</span><span class="sxs-lookup"><span data-stu-id="74410-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="74410-112">Par exemple, la touche Maj est représentée par <xref:System.Windows.Forms.Keys.Shift> <xref:System.Windows.Forms.Keys.RShiftKey> , <xref:System.Windows.Forms.Keys.ShiftKey>et <xref:System.Windows.Forms.Keys.LShiftKey> la valeur correcte pour tester Shift comme touche de modification est <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="74410-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="74410-113">De même, pour tester les touches Ctrl et Alt en tant que modificateurs, <xref:System.Windows.Forms.Keys.Control> vous <xref:System.Windows.Forms.Keys.Alt> devez utiliser respectivement les valeurs et.</span><span class="sxs-lookup"><span data-stu-id="74410-113">Similarly, to test for CTRL and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74410-114">Visual Basic programmeurs peuvent également accéder aux informations de clé <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> par le biais de la propriété</span><span class="sxs-lookup"><span data-stu-id="74410-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="74410-115">Pour déterminer la touche de modification qui a été enfoncée</span><span class="sxs-lookup"><span data-stu-id="74410-115">To determine which modifier key was pressed</span></span>  
  
- <span data-ttu-id="74410-116">Utilisez l’opérateur `AND` au niveau du <xref:System.Windows.Forms.Control.ModifierKeys%2A> bit avec la propriété et une <xref:System.Windows.Forms.Keys> valeur de l’énumération pour déterminer si une touche de modification particulière est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="74410-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="74410-117">L’exemple de code suivant montre comment déterminer si la touche Maj est enfoncée <xref:System.Windows.Forms.Control.KeyPress> dans un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="74410-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="74410-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74410-118">See also</span></span>

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [<span data-ttu-id="74410-119">Entrée au clavier dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74410-119">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- <span data-ttu-id="74410-120">[Guide pratique pour Déterminer si CapsLock est activé dans Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="74410-120">[How to: Determine If CapsLock is On in Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span></span>
