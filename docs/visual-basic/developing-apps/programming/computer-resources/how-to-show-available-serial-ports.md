---
title: 'Procédure : afficher les ports série disponibles'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: b19bdd56311ab7029fb224256d138a0dc0dd8ddc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557344"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="5d4eb-102">Guide pratique pour afficher les ports série disponibles en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d4eb-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="5d4eb-103">Cette rubrique explique comment utiliser `My.Computer.Ports` pour afficher les ports série disponibles sur l’ordinateur en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="5d4eb-104">Pour permettre à un utilisateur de sélectionner le port à utiliser, les noms des ports série sont placés dans un contrôle <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d4eb-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5d4eb-105">Example</span></span>  

 <span data-ttu-id="5d4eb-106">Cet exemple exécute une boucle sur toutes les chaînes retournées par la propriété `My.Computer.Ports.SerialPortNames`.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="5d4eb-107">Ces chaînes correspondent aux noms des ports série disponibles sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="5d4eb-108">En règle générale, un utilisateur sélectionne le port série que l’application doit utiliser dans la liste des ports disponibles.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="5d4eb-109">Dans cet exemple, les noms de port série sont stockés dans un contrôle <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="5d4eb-110">Pour plus d’informations, consultez [ListBox Control](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="5d4eb-110">For more information, see [ListBox Control](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="5d4eb-111">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="5d4eb-112">Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="5d4eb-113">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="5d4eb-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d4eb-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5d4eb-114">Compiling the Code</span></span>  

 <span data-ttu-id="5d4eb-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="5d4eb-115">This example requires:</span></span>  
  
- <span data-ttu-id="5d4eb-116">Une référence de projet à System.Windows.Forms.dll</span><span class="sxs-lookup"><span data-stu-id="5d4eb-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="5d4eb-117">Un accès aux membres de l’espace de noms <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="5d4eb-118">Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="5d4eb-119">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="5d4eb-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="5d4eb-120">Votre formulaire doit avoir un contrôle <xref:System.Windows.Forms.ListBox> nommé `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5d4eb-121">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="5d4eb-121">Robust Programming</span></span>  

 <span data-ttu-id="5d4eb-122">Vous n’avez pas besoin d’utiliser le contrôle <xref:System.Windows.Forms.ListBox> pour afficher les noms des ports série disponibles.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="5d4eb-123">À la place, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.ComboBox> ou autre.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="5d4eb-124">Si l’application n’a pas besoin d’une réponse de l’utilisateur, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.TextBox> pour afficher les informations.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d4eb-125">Les noms de port retournés par `My.Computer.Ports.SerialPortNames` peuvent ne pas être corrects sur Windows 98.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="5d4eb-126">Pour éviter les erreurs d’application, utilisez la gestion des exceptions, comme les instructions `Try...Catch...Finally` et `Using`, lorsque vous utilisez les noms de ports pour ouvrir des ports.</span><span class="sxs-lookup"><span data-stu-id="5d4eb-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4eb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d4eb-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="5d4eb-128">Procédure : passer des appels avec des modems attachés aux ports série</span><span class="sxs-lookup"><span data-stu-id="5d4eb-128">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="5d4eb-129">Procédure : envoyer des chaînes aux ports série</span><span class="sxs-lookup"><span data-stu-id="5d4eb-129">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="5d4eb-130">Procédure : recevoir des chaînes provenant des ports série</span><span class="sxs-lookup"><span data-stu-id="5d4eb-130">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
