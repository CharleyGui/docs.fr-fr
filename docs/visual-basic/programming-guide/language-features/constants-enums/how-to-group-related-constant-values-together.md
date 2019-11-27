---
title: 'Comment : regrouper les valeurs de constante connexes'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 151eefee4f69e1db8ba40f91334da8a051b95732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354033"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="3fd1d-102">Comment : regrouper les valeurs de constante connexes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fd1d-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="3fd1d-103">Une énumération est la meilleure façon de regrouper des constantes associées.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="3fd1d-104">Vous créez une énumération avec l’instruction `Enum` dans la section déclarations d’une classe ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="3fd1d-105">Pour plus d’informations, consultez [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="3fd1d-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="3fd1d-106">Pour regrouper des valeurs de constante associées</span><span class="sxs-lookup"><span data-stu-id="3fd1d-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="3fd1d-107">Écrivez une déclaration qui comprend un niveau d’accès au code, le mot clé `Enum` et un nom valide.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="3fd1d-108">Cet exemple crée l’énumération `Private`, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="3fd1d-109">Définissez les constantes dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="3fd1d-110">Cet exemple crée l’énumération `Public` `temperatureValues` et assigne ses valeurs.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3fd1d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fd1d-111">See also</span></span>

- [<span data-ttu-id="3fd1d-112">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="3fd1d-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="3fd1d-113">Guide pratique : faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="3fd1d-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="3fd1d-114">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="3fd1d-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="3fd1d-115">Vue d’ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="3fd1d-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="3fd1d-116">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="3fd1d-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="3fd1d-117">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="3fd1d-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
