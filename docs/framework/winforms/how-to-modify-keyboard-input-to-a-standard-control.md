---
title: 'Procédure : changer l’entrée de clavier en contrôle standard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 175296a904a6aed70147f513959fce74b3288abc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630487"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="69c59-102">Procédure : changer l’entrée de clavier en contrôle standard</span><span class="sxs-lookup"><span data-stu-id="69c59-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="69c59-103">Windows Forms offre la possibilité de consommer et de modifier l'entrée au clavier.</span><span class="sxs-lookup"><span data-stu-id="69c59-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="69c59-104">Consommer une touche signifie gérer une touche dans une méthode ou un gestionnaire d'événements pour que d'autres méthodes et événements plus loin dans la file d'attente de messages ne reçoivent pas la valeur de la touche.</span><span class="sxs-lookup"><span data-stu-id="69c59-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="69c59-105">Modifier une touche signifie modifier sa valeur pour que les méthodes et les gestionnaires d'événements plus loin dans la file d'attente de messages reçoivent une valeur de touche différente.</span><span class="sxs-lookup"><span data-stu-id="69c59-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="69c59-106">Cette rubrique montre comment accomplir ces tâches.</span><span class="sxs-lookup"><span data-stu-id="69c59-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="69c59-107">Pour consommer une touche</span><span class="sxs-lookup"><span data-stu-id="69c59-107">To consume a key</span></span>  
  
- <span data-ttu-id="69c59-108">Dans un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyPress>, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> de la classe <xref:System.Windows.Forms.KeyPressEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="69c59-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="69c59-109">ou</span><span class="sxs-lookup"><span data-stu-id="69c59-109">-or-</span></span>  
  
     <span data-ttu-id="69c59-110">Dans un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyDown>, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> de la classe <xref:System.Windows.Forms.KeyEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="69c59-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69c59-111">La définition de la propriété <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyDown> n'empêche pas les événements <xref:System.Windows.Forms.Control.KeyPress> et <xref:System.Windows.Forms.Control.KeyUp> d'être déclenchés pour la séquence de touches actuelle.</span><span class="sxs-lookup"><span data-stu-id="69c59-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="69c59-112">Vous devez pour cela utiliser la propriété <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A>.</span><span class="sxs-lookup"><span data-stu-id="69c59-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="69c59-113">L'exemple suivant est un extrait d'instruction `switch` qui examine la propriété <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> du <xref:System.Windows.Forms.KeyPressEventArgs> reçu par un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyPress>.</span><span class="sxs-lookup"><span data-stu-id="69c59-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="69c59-114">Ce code consomme les touches de caractère « A » et « a ».</span><span class="sxs-lookup"><span data-stu-id="69c59-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="69c59-115">Pour modifier une touche de caractère standard</span><span class="sxs-lookup"><span data-stu-id="69c59-115">To modify a standard character key</span></span>  
  
- <span data-ttu-id="69c59-116">Dans un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyPress>, affectez à la propriété <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> de la classe <xref:System.Windows.Forms.KeyPressEventArgs> la valeur de la nouvelle touche de caractère.</span><span class="sxs-lookup"><span data-stu-id="69c59-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="69c59-117">L'exemple suivant est un extrait d'instruction `switch` qui remplace « B » par « A » et « b » par « a ».</span><span class="sxs-lookup"><span data-stu-id="69c59-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="69c59-118">Notez que la propriété <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> du paramètre <xref:System.Windows.Forms.KeyPressEventArgs> a la valeur `false`, pour que la nouvelle valeur de touche soit propagée aux autres méthodes et événements dans la file d'attente de messages.</span><span class="sxs-lookup"><span data-stu-id="69c59-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="69c59-119">Pour modifier une touche non-caractère</span><span class="sxs-lookup"><span data-stu-id="69c59-119">To modify a noncharacter key</span></span>  
  
- <span data-ttu-id="69c59-120">Substituez une méthode <xref:System.Windows.Forms.Control> qui traite les messages Windows, détectez le message WM_KEYDOWN ou WM_SYSKEYDOWN et affectez à la propriété <xref:System.Windows.Forms.Message.WParam%2A> du paramètre <xref:System.Windows.Forms.Message> la valeur <xref:System.Windows.Forms.Keys> qui représente la nouvelle touche non-caractère.</span><span class="sxs-lookup"><span data-stu-id="69c59-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="69c59-121">L'exemple de code suivant montre comment substituer la méthode <xref:System.Windows.Forms.Control.PreProcessMessage%2A> d'un contrôle pour détecter les touches F1 à F9 et modifier toute activation de la touche F3 en F1.</span><span class="sxs-lookup"><span data-stu-id="69c59-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="69c59-122">Pour plus d’informations sur <xref:System.Windows.Forms.Control> méthodes que vous pouvez substituer pour intercepter des messages de clavier, consultez [entrée d’utilisateur dans une Application de formulaires Windows](user-input-in-a-windows-forms-application.md) et [fonctionnement des entrées au clavier](how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="69c59-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="69c59-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="69c59-123">Example</span></span>  
 <span data-ttu-id="69c59-124">L'exemple de code suivant est l'application complète pour les exemples de code des sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="69c59-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="69c59-125">L'application utilise un contrôle personnalisé dérivé de la classe <xref:System.Windows.Forms.TextBox> pour consommer et modifier l'entrée au clavier.</span><span class="sxs-lookup"><span data-stu-id="69c59-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69c59-126">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="69c59-126">Compiling the Code</span></span>  
 <span data-ttu-id="69c59-127">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="69c59-127">This example requires:</span></span>  
  
- <span data-ttu-id="69c59-128">des références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="69c59-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="69c59-129">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="69c59-129">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="69c59-130">Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="69c59-130">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c59-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69c59-131">See also</span></span>

- [<span data-ttu-id="69c59-132">Entrée au clavier dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69c59-132">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="69c59-133">Entrée d’utilisateur dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69c59-133">User Input in a Windows Forms Application</span></span>](user-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="69c59-134">Fonctionnement de l’entrée au clavier</span><span class="sxs-lookup"><span data-stu-id="69c59-134">How Keyboard Input Works</span></span>](how-keyboard-input-works.md)
