---
title: 'Guide pratique : itérer au sein d’une énumération'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414425"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="0c791-102">Comment : itérer au sein d'une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c791-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="0c791-103">Les énumérations offrent un moyen pratique de travailler avec des ensembles de constantes connexes et d’associer des valeurs de constantes à des noms.</span><span class="sxs-lookup"><span data-stu-id="0c791-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="0c791-104">Pour itérer au sein d’une énumération, vous pouvez la déplacer dans un tableau à l’aide de la <xref:System.Enum.GetValues%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="0c791-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="0c791-105">Vous pouvez également itérer au sein d’une énumération à l’aide d’une `For...Each` instruction, en utilisant la <xref:System.Enum.GetNames%2A> <xref:System.Enum.GetValues%2A> méthode ou pour extraire la chaîne ou la valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="0c791-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="0c791-106">Pour itérer au sein d’une énumération</span><span class="sxs-lookup"><span data-stu-id="0c791-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="0c791-107">Déclarez un tableau et convertissez-le en l’énumération avec la <xref:System.Enum.GetValues%2A> méthode avant de passer le tableau comme vous le feriez pour toute autre variable.</span><span class="sxs-lookup"><span data-stu-id="0c791-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="0c791-108">L’exemple suivant affiche chaque membre de l’énumération au <xref:Microsoft.VisualBasic.FirstDayOfWeek> fur et à mesure qu’il itère au sein de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="0c791-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0c791-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c791-109">See also</span></span>

- [<span data-ttu-id="0c791-110">Vue d'ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="0c791-110">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="0c791-111">How to: Declare an, énumération</span><span class="sxs-lookup"><span data-stu-id="0c791-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="0c791-112">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="0c791-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="0c791-113">Comment : déterminer la chaîne associée à une valeur d'énumération</span><span class="sxs-lookup"><span data-stu-id="0c791-113">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="0c791-114">Comment : faire référence à un membre d'énumération</span><span class="sxs-lookup"><span data-stu-id="0c791-114">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="0c791-115">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="0c791-115">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="0c791-116">Tableaux</span><span class="sxs-lookup"><span data-stu-id="0c791-116">Arrays</span></span>](../arrays/index.md)
