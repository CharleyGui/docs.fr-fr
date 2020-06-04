---
title: "Comment : déterminer la chaîne associée à une valeur d'énumération"
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 525da9206472afefa9f85b49ceee0775cbd168c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414464"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="035a2-102">Comment : déterminer la chaîne associée à une valeur d'énumération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="035a2-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="035a2-103">Les <xref:System.Enum.GetValues%2A> <xref:System.Enum.GetNames%2A> méthodes et vous permettent de déterminer les chaînes et les valeurs associées aux membres de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="035a2-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="035a2-104">Pour déterminer la chaîne associée à une énumération</span><span class="sxs-lookup"><span data-stu-id="035a2-104">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="035a2-105">Utilisez la <xref:System.Enum.GetNames%2A> méthode pour récupérer les chaînes associées aux membres de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="035a2-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="035a2-106">Cet exemple déclare une énumération, `flavorEnum` , puis utilise la <xref:System.Enum.GetNames%2A> méthode pour afficher les chaînes associées à chaque membre.</span><span class="sxs-lookup"><span data-stu-id="035a2-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="035a2-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="035a2-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="035a2-108">How to: Declare an, énumération</span><span class="sxs-lookup"><span data-stu-id="035a2-108">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="035a2-109">Comment : faire référence à un membre d'énumération</span><span class="sxs-lookup"><span data-stu-id="035a2-109">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="035a2-110">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="035a2-110">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="035a2-111">Comment : itérer au sein d'une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="035a2-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="035a2-112">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="035a2-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="035a2-113">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="035a2-113">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
