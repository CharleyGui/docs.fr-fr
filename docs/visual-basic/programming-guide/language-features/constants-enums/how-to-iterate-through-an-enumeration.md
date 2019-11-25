---
title: 'How to: Iterate Through An Enumeration'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 6e8fd6760565a73d9d3b3d1d02fc872992eea354
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354020"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="e8438-102">Comment : itérer au sein d'une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8438-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="e8438-103">Les énumérations offrent un moyen pratique de travailler avec des ensembles de constantes connexes et d’associer des valeurs de constantes à des noms.</span><span class="sxs-lookup"><span data-stu-id="e8438-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="e8438-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span><span class="sxs-lookup"><span data-stu-id="e8438-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="e8438-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span><span class="sxs-lookup"><span data-stu-id="e8438-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="e8438-106">To iterate through an enumeration</span><span class="sxs-lookup"><span data-stu-id="e8438-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="e8438-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span><span class="sxs-lookup"><span data-stu-id="e8438-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="e8438-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span><span class="sxs-lookup"><span data-stu-id="e8438-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="e8438-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8438-109">See also</span></span>

- [<span data-ttu-id="e8438-110">Vue d’ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="e8438-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="e8438-111">How to: Declare an Enumeration</span><span class="sxs-lookup"><span data-stu-id="e8438-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="e8438-112">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="e8438-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="e8438-113">Guide pratique : déterminer la chaîne associée à une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="e8438-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="e8438-114">Guide pratique : faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="e8438-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="e8438-115">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="e8438-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="e8438-116">Tableaux</span><span class="sxs-lookup"><span data-stu-id="e8438-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
