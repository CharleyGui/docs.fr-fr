---
title: 'Comment : recevoir des chaînes des ports série'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345600"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="62fd8-102">Guide pratique pour recevoir des chaînes provenant des ports série en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62fd8-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="62fd8-103">Cette rubrique explique comment utiliser `My.Computer.Ports` pour recevoir des chaînes provenant des ports série de l’ordinateur en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="62fd8-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="62fd8-104">Pour recevoir des chaînes provenant d’un port série</span><span class="sxs-lookup"><span data-stu-id="62fd8-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="62fd8-105">Initialisez la chaîne de retour.</span><span class="sxs-lookup"><span data-stu-id="62fd8-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="62fd8-106">Déterminez quel port série doit fournir les chaînes.</span><span class="sxs-lookup"><span data-stu-id="62fd8-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="62fd8-107">Cet exemple suppose qu’il s’agit de `COM1`.</span><span class="sxs-lookup"><span data-stu-id="62fd8-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="62fd8-108">Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.</span><span class="sxs-lookup"><span data-stu-id="62fd8-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="62fd8-109">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="62fd8-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="62fd8-110">Le bloc `Try...Catch...Finally` permet à l’application de fermer le port série, même si cela génère une exception.</span><span class="sxs-lookup"><span data-stu-id="62fd8-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="62fd8-111">Tout le code qui manipule le port série doit apparaître dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="62fd8-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="62fd8-112">Créez une boucle `Do` pour lire les lignes de texte jusqu’à ce que plus aucune ligne ne soit disponible.</span><span class="sxs-lookup"><span data-stu-id="62fd8-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="62fd8-113">Utilisez la méthode <xref:System.IO.Ports.SerialPort.ReadLine> pour lire la ligne de texte disponible suivante à partir du port série.</span><span class="sxs-lookup"><span data-stu-id="62fd8-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="62fd8-114">Utilisez une instruction `If` pour déterminer si la méthode <xref:System.IO.Ports.SerialPort.ReadLine> retourne `Nothing` (ce qui signifie qu’il n’y a plus de texte disponible).</span><span class="sxs-lookup"><span data-stu-id="62fd8-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="62fd8-115">Si elle retourne `Nothing`, quittez la boucle `Do`.</span><span class="sxs-lookup"><span data-stu-id="62fd8-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="62fd8-116">Ajoutez un bloc `Else` à l’instruction `If` pour gérer la situation si la chaîne est lue.</span><span class="sxs-lookup"><span data-stu-id="62fd8-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="62fd8-117">Le bloc ajoute la chaîne du port série à la chaîne de retour.</span><span class="sxs-lookup"><span data-stu-id="62fd8-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="62fd8-118">Retourne la chaîne.</span><span class="sxs-lookup"><span data-stu-id="62fd8-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="62fd8-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="62fd8-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="62fd8-120">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="62fd8-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="62fd8-121">Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**.</span><span class="sxs-lookup"><span data-stu-id="62fd8-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="62fd8-122">Pour plus d'informations, consultez [Code Snippets](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="62fd8-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62fd8-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="62fd8-123">Compiling the Code</span></span>  

 <span data-ttu-id="62fd8-124">Cet exemple suppose que l’ordinateur utilise `COM1`.</span><span class="sxs-lookup"><span data-stu-id="62fd8-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="62fd8-125">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="62fd8-125">Robust Programming</span></span>  

 <span data-ttu-id="62fd8-126">Cet exemple suppose que l’ordinateur utilise `COM1`.</span><span class="sxs-lookup"><span data-stu-id="62fd8-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="62fd8-127">Pour plus de souplesse, le code doit autoriser l’utilisateur à sélectionner le port série dans la liste des ports disponibles.</span><span class="sxs-lookup"><span data-stu-id="62fd8-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="62fd8-128">Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="62fd8-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="62fd8-129">Cet exemple utilise un bloc `Try...Catch...Finally` pour garantir que l’application ferme le port et intercepte les exceptions d’expiration.</span><span class="sxs-lookup"><span data-stu-id="62fd8-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="62fd8-130">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="62fd8-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62fd8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62fd8-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="62fd8-132">Guide pratique : passer des appels avec des modems attachés aux ports série</span><span class="sxs-lookup"><span data-stu-id="62fd8-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="62fd8-133">Guide pratique : envoyer des chaînes aux ports série</span><span class="sxs-lookup"><span data-stu-id="62fd8-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="62fd8-134">Guide pratique pour afficher les ports série disponibles</span><span class="sxs-lookup"><span data-stu-id="62fd8-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
