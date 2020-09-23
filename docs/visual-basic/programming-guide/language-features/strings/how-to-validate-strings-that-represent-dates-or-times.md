---
title: 'Comment : valider des chaînes qui représentent des dates ou des heures'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f3654894e274404410179dab04422e20f6040440
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072598"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="55905-102">Comment : valider des chaînes qui représentent des dates ou des heures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55905-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>

<span data-ttu-id="55905-103">L’exemple de code suivant définit une `Boolean` valeur qui indique si une chaîne représente une date ou une heure valide.</span><span class="sxs-lookup"><span data-stu-id="55905-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55905-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="55905-104">Example</span></span>  

 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="55905-105">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="55905-105">Compile the code</span></span>  

 <span data-ttu-id="55905-106">Remplacez `("01/01/03")` et `"9:30 PM"` par la date et l’heure que vous souhaitez valider.</span><span class="sxs-lookup"><span data-stu-id="55905-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="55905-107">Vous pouvez remplacer la chaîne par une autre chaîne codée en dur, par une `String` variable ou par une méthode qui retourne une chaîne, telle que `InputBox` .</span><span class="sxs-lookup"><span data-stu-id="55905-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="55905-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="55905-108">Robust Programming</span></span>  

 <span data-ttu-id="55905-109">Utilisez cette méthode pour valider la chaîne avant d’essayer de convertir `String` en une `DateTime` variable.</span><span class="sxs-lookup"><span data-stu-id="55905-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="55905-110">En vérifiant d’abord la date ou l’heure, vous pouvez éviter de générer une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="55905-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55905-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55905-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="55905-112">Validation de chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55905-112">Validating Strings in Visual Basic</span></span>](validating-strings.md)
