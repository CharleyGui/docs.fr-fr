---
title: 'Procédure : Faire référence à un membre d’énumération (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 000c7f8f87792b598f177cae123010eb8888c328
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645968"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="86f0e-102">Procédure : Faire référence à un membre d’énumération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86f0e-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="86f0e-103">Les énumérations offrent un moyen pratique d’utiliser des ensembles de constantes connexes et d’associer des valeurs constantes avec des noms.</span><span class="sxs-lookup"><span data-stu-id="86f0e-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="86f0e-104">Par exemple, vous pouvez déclarer une énumération pour un ensemble de constantes entières associées aux jours de la semaine puis utiliser les noms des jours au lieu de leur valeur entière dans votre code.</span><span class="sxs-lookup"><span data-stu-id="86f0e-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="86f0e-105">Vous pouvez éviter d’utiliser des noms qualifiés complets avec la `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="86f0e-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="86f0e-106">Pour plus d’informations, consultez [énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="86f0e-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="86f0e-107">Pour faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="86f0e-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="86f0e-108">Qualifier le nom du membre de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="86f0e-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="86f0e-109">Par exemple, l’exemple suivant affecte la `Saturday` membre de la `FirstDayOfWeek` énumération à la variable `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="86f0e-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="86f0e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86f0e-110">See also</span></span>

- [<span data-ttu-id="86f0e-111">Guide pratique pour Déclarer une énumération</span><span class="sxs-lookup"><span data-stu-id="86f0e-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="86f0e-112">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="86f0e-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="86f0e-113">Guide pratique pour Parcourir une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86f0e-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="86f0e-114">Guide pratique pour Déterminer la chaîne associée à une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="86f0e-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="86f0e-115">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="86f0e-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
