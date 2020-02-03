---
title: Gérer les événements d’entrée d’utilisateur dans les contrôles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 19adeb6c803c76cba4139841f58087487d523a50
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739417"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="8abad-102">Comment : gérer des événements d'entrée d'utilisateur dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8abad-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="8abad-103">Cet exemple montre comment gérer la plupart des événements de clavier, de souris, de focus et de validation qui peuvent se produire dans un contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8abad-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="8abad-104">La zone de texte nommée `TextBoxInput` reçoit les événements quand elle a le focus et les informations relatives à chaque événement sont écrites dans la zone de texte nommée `TextBoxOutput` dans l'ordre dans lequel les événements sont déclenchés.</span><span class="sxs-lookup"><span data-stu-id="8abad-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="8abad-105">L'application comprend également un ensemble de cases à cocher qui peuvent servir à filtrer les événements pour lesquels établir un rapport.</span><span class="sxs-lookup"><span data-stu-id="8abad-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8abad-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="8abad-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8abad-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8abad-107">Compiling the Code</span></span>  
 <span data-ttu-id="8abad-108">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="8abad-108">This example requires:</span></span>  
  
- <span data-ttu-id="8abad-109">des références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8abad-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8abad-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8abad-110">See also</span></span>

- [<span data-ttu-id="8abad-111">Entrée d’utilisateur dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8abad-111">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
