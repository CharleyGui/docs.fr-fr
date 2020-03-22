---
title: 'Comment : envoyer des chaînes aux ports série'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: b2051451142a7818a3b7d1bc564c5ae36b2579fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345584"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="41dbb-102">Guide pratique pour envoyer des chaînes aux ports série en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41dbb-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="41dbb-103">Cette rubrique explique comment utiliser `My.Computer.Ports` pour envoyer des chaînes aux ports série de l’ordinateur en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="41dbb-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41dbb-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="41dbb-104">Example</span></span>  

 <span data-ttu-id="41dbb-105">Cet exemple envoie une chaîne au port série COM1.</span><span class="sxs-lookup"><span data-stu-id="41dbb-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="41dbb-106">Vous devrez peut-être utiliser un autre port série de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="41dbb-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="41dbb-107">Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.</span><span class="sxs-lookup"><span data-stu-id="41dbb-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="41dbb-108">Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="41dbb-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="41dbb-109">Le bloc `Using` permet à l’application de fermer le port série, même si cela génère une exception.</span><span class="sxs-lookup"><span data-stu-id="41dbb-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="41dbb-110">Tout le code qui manipule le port série doit apparaître dans ce bloc, ou dans un bloc `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="41dbb-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="41dbb-111">La méthode <xref:System.IO.Ports.SerialPort.WriteLine%2A> envoie les données au port série.</span><span class="sxs-lookup"><span data-stu-id="41dbb-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41dbb-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="41dbb-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="41dbb-113">Cet exemple suppose que l’ordinateur utilise `COM1`.</span><span class="sxs-lookup"><span data-stu-id="41dbb-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="41dbb-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="41dbb-114">Robust Programming</span></span>  

 <span data-ttu-id="41dbb-115">Cet exemple suppose que l’ordinateur utilise `COM1`. Pour plus de souplesse, le code doit autoriser l’utilisateur à sélectionner le port série dans la liste des ports disponibles.</span><span class="sxs-lookup"><span data-stu-id="41dbb-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="41dbb-116">Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="41dbb-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="41dbb-117">Cet exemple utilise un bloc `Using` pour garantir que l’application ferme le port même si elle lève une exception.</span><span class="sxs-lookup"><span data-stu-id="41dbb-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="41dbb-118">Pour plus d’informations, voir [Utilisation de l’instruction](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="41dbb-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dbb-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41dbb-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="41dbb-120">Comment : passer des appels avec des modems attachés aux ports série</span><span class="sxs-lookup"><span data-stu-id="41dbb-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="41dbb-121">Comment : afficher les ports série disponibles</span><span class="sxs-lookup"><span data-stu-id="41dbb-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
