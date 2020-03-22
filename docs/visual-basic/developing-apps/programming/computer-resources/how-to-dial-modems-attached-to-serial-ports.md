---
title: 'Comment : passer des appels avec des modems attachés aux ports série'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345637"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="4bc24-102">Guide pratique pour passer des appels avec des modems attachés aux ports série dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4bc24-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="4bc24-103">Cette rubrique explique comment utiliser `My.Computer.Ports` pour passer un appel avec un modem dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4bc24-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="4bc24-104">En règle générale, le modem est connecté à l’un des ports série sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4bc24-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="4bc24-105">Pour que l’application puisse communiquer avec le modem, elle doit envoyer des commandes au port série approprié.</span><span class="sxs-lookup"><span data-stu-id="4bc24-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="4bc24-106">Pour communiquer avec un modem</span><span class="sxs-lookup"><span data-stu-id="4bc24-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="4bc24-107">Déterminez le port série auquel le modem est connecté.</span><span class="sxs-lookup"><span data-stu-id="4bc24-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="4bc24-108">Cet exemple part du principe que le modem est connecté à COM1.</span><span class="sxs-lookup"><span data-stu-id="4bc24-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="4bc24-109">Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.</span><span class="sxs-lookup"><span data-stu-id="4bc24-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="4bc24-110">Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="4bc24-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="4bc24-111">Le bloc `Using` permet à l’application de fermer le port série, même si cela génère une exception.</span><span class="sxs-lookup"><span data-stu-id="4bc24-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="4bc24-112">Tout le code qui manipule le port série doit apparaître dans ce bloc, ou dans un bloc `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="4bc24-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="4bc24-113">Définissez la propriété `DtrEnable` pour indiquer que l’ordinateur est prêt à accepter une transmission en provenance du modem.</span><span class="sxs-lookup"><span data-stu-id="4bc24-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="4bc24-114">Envoyez la commande de numérotation et le numéro de téléphone au modem par l’intermédiaire du port série à l’aide de la méthode <xref:System.IO.Ports.SerialPort.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="4bc24-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="4bc24-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="4bc24-115">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="4bc24-116">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4bc24-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4bc24-117">Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**.</span><span class="sxs-lookup"><span data-stu-id="4bc24-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="4bc24-118">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="4bc24-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4bc24-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4bc24-119">Compiling the Code</span></span>  

 <span data-ttu-id="4bc24-120">Cet exemple nécessite une référence à l’espace de noms <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4bc24-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4bc24-121">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="4bc24-121">Robust Programming</span></span>  

 <span data-ttu-id="4bc24-122">Cet exemple part du principe que le modem est connecté à COM1.</span><span class="sxs-lookup"><span data-stu-id="4bc24-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="4bc24-123">Nous recommandons que le code autorise l’utilisateur à sélectionner le port série dans la liste des ports disponibles.</span><span class="sxs-lookup"><span data-stu-id="4bc24-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="4bc24-124">Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="4bc24-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="4bc24-125">Cet exemple utilise un bloc `Using` pour garantir que l’application ferme le port même si elle lève une exception.</span><span class="sxs-lookup"><span data-stu-id="4bc24-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="4bc24-126">Pour plus d’informations, voir [Utilisation de l’instruction](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4bc24-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="4bc24-127">Dans cet exemple, l’application déconnecte le port série après avoir utilisé le modem.</span><span class="sxs-lookup"><span data-stu-id="4bc24-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="4bc24-128">Dans la pratique, vous souhaiterez transférer des données vers et à partir du modem.</span><span class="sxs-lookup"><span data-stu-id="4bc24-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="4bc24-129">Pour plus d’informations, consultez [Guide pratique pour recevoir des chaînes des ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="4bc24-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bc24-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bc24-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="4bc24-131">Comment : envoyer des chaînes aux ports série</span><span class="sxs-lookup"><span data-stu-id="4bc24-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="4bc24-132">Comment : recevoir des chaînes des ports série</span><span class="sxs-lookup"><span data-stu-id="4bc24-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="4bc24-133">Comment : afficher les ports série disponibles</span><span class="sxs-lookup"><span data-stu-id="4bc24-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
