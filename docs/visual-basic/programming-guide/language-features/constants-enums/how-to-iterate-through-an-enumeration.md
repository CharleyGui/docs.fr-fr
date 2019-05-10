---
title: 'Procédure : Parcourir une énumération dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: c3fd7e6f7e8e4fcabf279975f7ffc2d848679396
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645246"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="530a4-102">Procédure : Parcourir une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="530a4-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="530a4-103">Les énumérations offrent un moyen pratique de travailler avec des ensembles de constantes connexes et d’associer des valeurs de constantes à des noms.</span><span class="sxs-lookup"><span data-stu-id="530a4-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="530a4-104">Pour parcourir une énumération, vous pouvez la déplacer dans un tableau à l’aide de la <xref:System.Enum.GetValues%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="530a4-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="530a4-105">Vous pouvez également itérer sur une énumération à l’aide un `For...Each` instruction, à l’aide de la <xref:System.Enum.GetNames%2A> ou <xref:System.Enum.GetValues%2A> méthode pour extraire la valeur de chaîne ou numérique.</span><span class="sxs-lookup"><span data-stu-id="530a4-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="530a4-106">Pour effectuer une itération dans une énumération</span><span class="sxs-lookup"><span data-stu-id="530a4-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="530a4-107">Déclarez un tableau et convertissez l’énumération avec la <xref:System.Enum.GetValues%2A> méthode avant de passer le tableau en tant que vous aurait de toute autre variable.</span><span class="sxs-lookup"><span data-stu-id="530a4-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="530a4-108">L’exemple suivant affiche chaque membre de l’énumération <xref:Microsoft.VisualBasic.FirstDayOfWeek> itère l’énumération.</span><span class="sxs-lookup"><span data-stu-id="530a4-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="530a4-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="530a4-109">See also</span></span>

- [<span data-ttu-id="530a4-110">Vue d’ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="530a4-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="530a4-111">Guide pratique pour Déclarer une énumération</span><span class="sxs-lookup"><span data-stu-id="530a4-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="530a4-112">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="530a4-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="530a4-113">Guide pratique pour Déterminer la chaîne associée à une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="530a4-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="530a4-114">Guide pratique pour Faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="530a4-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="530a4-115">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="530a4-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="530a4-116">Tableaux</span><span class="sxs-lookup"><span data-stu-id="530a4-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
