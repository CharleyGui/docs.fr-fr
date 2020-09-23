---
title: "Comment : faire référence à un membre d'énumération"
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: d1b239e7d6be3ebf1e64d6589a4cc14dce8946f5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095666"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="39dd7-102">Comment : faire référence à un membre d'énumération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39dd7-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>

<span data-ttu-id="39dd7-103">Les énumérations offrent un moyen pratique d’utiliser des ensembles de constantes associées et d’associer des valeurs constantes à des noms.</span><span class="sxs-lookup"><span data-stu-id="39dd7-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="39dd7-104">Par exemple, vous pouvez déclarer une énumération pour un ensemble de constantes entières associées aux jours de la semaine puis utiliser les noms des jours au lieu de leur valeur entière dans votre code.</span><span class="sxs-lookup"><span data-stu-id="39dd7-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="39dd7-105">Vous pouvez éviter d’utiliser des noms qualifiés complets avec l' `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="39dd7-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="39dd7-106">Pour plus d’informations, consultez [énumérations et qualification de nom](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="39dd7-106">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="39dd7-107">Pour faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="39dd7-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="39dd7-108">Qualifiez le nom de membre avec l’énumération.</span><span class="sxs-lookup"><span data-stu-id="39dd7-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="39dd7-109">Par exemple, l’exemple suivant affecte le `Saturday` membre de l' `FirstDayOfWeek` énumération à la variable `DayValue` .</span><span class="sxs-lookup"><span data-stu-id="39dd7-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="39dd7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39dd7-110">See also</span></span>

- [<span data-ttu-id="39dd7-111">How to: Declare an, énumération</span><span class="sxs-lookup"><span data-stu-id="39dd7-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="39dd7-112">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="39dd7-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="39dd7-113">Comment : itérer au sein d'une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39dd7-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="39dd7-114">Comment : déterminer la chaîne associée à une valeur d'énumération</span><span class="sxs-lookup"><span data-stu-id="39dd7-114">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="39dd7-115">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="39dd7-115">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
