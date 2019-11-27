---
title: "Comment : faire référence à un membre d'énumération"
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 01db5b84783eda45cd7867dc8fea8a69fc18b98a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354000"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="4df64-102">Comment : faire référence à un membre d'énumération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4df64-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="4df64-103">Les énumérations offrent un moyen pratique d’utiliser des ensembles de constantes associées et d’associer des valeurs constantes à des noms.</span><span class="sxs-lookup"><span data-stu-id="4df64-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="4df64-104">Par exemple, vous pouvez déclarer une énumération pour un ensemble de constantes entières associées aux jours de la semaine puis utiliser les noms des jours au lieu de leur valeur entière dans votre code.</span><span class="sxs-lookup"><span data-stu-id="4df64-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="4df64-105">Vous pouvez éviter d’utiliser des noms qualifiés complets avec l’instruction `Imports`.</span><span class="sxs-lookup"><span data-stu-id="4df64-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="4df64-106">Pour plus d’informations, consultez [énumérations et qualification de nom](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="4df64-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="4df64-107">Pour faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="4df64-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="4df64-108">Qualifiez le nom de membre avec l’énumération.</span><span class="sxs-lookup"><span data-stu-id="4df64-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="4df64-109">Par exemple, l’exemple suivant affecte le membre `Saturday` de l’énumération `FirstDayOfWeek` à la variable `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="4df64-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="4df64-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4df64-110">See also</span></span>

- [<span data-ttu-id="4df64-111">Comment : déclarer une énumération</span><span class="sxs-lookup"><span data-stu-id="4df64-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="4df64-112">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="4df64-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="4df64-113">Comment : itérer au sein d’une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4df64-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="4df64-114">Guide pratique : déterminer la chaîne associée à une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="4df64-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="4df64-115">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="4df64-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
