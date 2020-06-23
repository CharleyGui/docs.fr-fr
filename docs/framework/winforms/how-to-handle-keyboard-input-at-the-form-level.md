---
title: 'Procédure : gérer l’entrée de clavier au niveau du formulaire'
description: Apprenez à gérer l’entrée au clavier pour votre Windows Forms au niveau du formulaire, avant que les messages n’atteignent un contrôle.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904154"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="e3435-103">Procédure : gérer l’entrée de clavier au niveau du formulaire</span><span class="sxs-lookup"><span data-stu-id="e3435-103">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="e3435-104">Windows Forms offre la possibilité de gérer les messages de clavier au niveau du formulaire, avant que les messages n'atteignent un contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3435-104">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="e3435-105">Cette rubrique montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="e3435-105">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="e3435-106">Pour gérer un message de clavier au niveau du formulaire</span><span class="sxs-lookup"><span data-stu-id="e3435-106">To handle a keyboard message at the form level</span></span>  
  
- <span data-ttu-id="e3435-107">Gérez l'événement <xref:System.Windows.Forms.Control.KeyPress> ou <xref:System.Windows.Forms.Control.KeyDown> du formulaire de démarrage et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Form.KeyPreview%2A> du formulaire pour que les messages de clavier soient reçus par le formulaire avant qu'ils atteignent les contrôles sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="e3435-107">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="e3435-108">L'exemple de code suivant gère l'événement <xref:System.Windows.Forms.Control.KeyPress> en détectant toutes les touches numériques et en consommant « 1 », « 4 » et « 7 ».</span><span class="sxs-lookup"><span data-stu-id="e3435-108">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="e3435-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3435-109">Example</span></span>  
 <span data-ttu-id="e3435-110">L'exemple de code suivant est l'application complète pour l'exemple ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="e3435-110">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="e3435-111">L'application comprend un <xref:System.Windows.Forms.TextBox> avec plusieurs autres contrôles qui vous permettent de déplacer le focus hors du <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e3435-111">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="e3435-112">L'événement <xref:System.Windows.Forms.Control.KeyPress> du <xref:System.Windows.Forms.Form> principal consomme « 1 », « 4 » et « 7 » et l'événement <xref:System.Windows.Forms.Control.KeyPress> du <xref:System.Windows.Forms.TextBox> consomme « 2 », « 5 » et « 8 » tout en affichant les touches restantes.</span><span class="sxs-lookup"><span data-stu-id="e3435-112">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="e3435-113">Comparez la sortie de <xref:System.Windows.Forms.MessageBox> quand vous appuyez sur une touche numérique pendant que le <xref:System.Windows.Forms.TextBox> a le focus avec la sortie de <xref:System.Windows.Forms.MessageBox> quand vous appuyez sur une touche numérique pendant que le focus est sur l'un des autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="e3435-113">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e3435-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e3435-114">Compiling the Code</span></span>  
 <span data-ttu-id="e3435-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="e3435-115">This example requires:</span></span>  
  
- <span data-ttu-id="e3435-116">des références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e3435-116">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3435-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3435-117">See also</span></span>

- [<span data-ttu-id="e3435-118">Entrée au clavier dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3435-118">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
