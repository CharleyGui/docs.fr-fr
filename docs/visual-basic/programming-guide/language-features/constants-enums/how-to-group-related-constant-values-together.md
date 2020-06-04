---
title: 'Comment : regrouper les valeurs de constante connexes'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: d2393af8b0c2b0c2e528f9908a78fbc7f182c8cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414438"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="f1645-102">Comment : regrouper les valeurs de constante connexes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1645-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="f1645-103">Une énumération est la meilleure façon de regrouper des constantes associées.</span><span class="sxs-lookup"><span data-stu-id="f1645-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="f1645-104">Vous créez une énumération avec l' `Enum` instruction dans la section déclarations d’une classe ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="f1645-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="f1645-105">Pour plus d’informations, consultez [Comment : déclarer une énumération](how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="f1645-105">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="f1645-106">Pour regrouper des valeurs de constante associées</span><span class="sxs-lookup"><span data-stu-id="f1645-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="f1645-107">Écrivez une déclaration qui comprend un niveau d’accès au code, le `Enum` mot clé et un nom valide.</span><span class="sxs-lookup"><span data-stu-id="f1645-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="f1645-108">Cet exemple crée l' `Private` énumération, `temperatureValues` .</span><span class="sxs-lookup"><span data-stu-id="f1645-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="f1645-109">Définissez les constantes dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="f1645-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="f1645-110">Cet exemple crée l' `Public` énumération `temperatureValues` et assigne ses valeurs.</span><span class="sxs-lookup"><span data-stu-id="f1645-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f1645-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1645-111">See also</span></span>

- [<span data-ttu-id="f1645-112">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="f1645-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="f1645-113">Comment : faire référence à un membre d'énumération</span><span class="sxs-lookup"><span data-stu-id="f1645-113">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="f1645-114">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="f1645-114">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="f1645-115">Vue d'ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="f1645-115">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="f1645-116">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="f1645-116">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="f1645-117">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="f1645-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
