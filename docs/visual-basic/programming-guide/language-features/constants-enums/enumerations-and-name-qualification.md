---
title: Énumérations et qualification de noms
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 6e067d72e557b97f8626b148e173e3d1583f92b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086268"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="bcd90-102">Énumérations et qualification de noms (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcd90-102">Enumerations and Name Qualification (Visual Basic)</span></span>

<span data-ttu-id="bcd90-103">Normalement, lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="bcd90-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="bcd90-104">Par exemple, pour faire référence au `Sunday` membre de votre `Days` énumération, vous devez utiliser la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="bcd90-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="bcd90-105">Utilisation de l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="bcd90-105">Using the Imports Statement</span></span>  

 <span data-ttu-id="bcd90-106">Vous pouvez éviter d’utiliser des noms qualifiés complets en ajoutant une `Imports` instruction à la section déclarations d’espace de noms de votre code, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bcd90-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="bcd90-107">Une `Imports` instruction importe des noms d’espaces de noms à partir de projets et d’assemblys référencés et dans le même projet que le module dans lequel l’instruction apparaît.</span><span class="sxs-lookup"><span data-stu-id="bcd90-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="bcd90-108">Une fois cette instruction ajoutée, vous pouvez faire référence à vos membres de l’énumération sans qualification, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bcd90-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="bcd90-109">En organisant des ensembles de constantes associées dans des énumérations, vous pouvez utiliser les mêmes noms de constantes dans des contextes différents.</span><span class="sxs-lookup"><span data-stu-id="bcd90-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="bcd90-110">Par exemple, vous pouvez utiliser les mêmes noms pour les constantes de jour de la semaine dans les `Days` `WorkDays` énumérations et.</span><span class="sxs-lookup"><span data-stu-id="bcd90-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="bcd90-111">Si vous utilisez l' `Imports` instruction avec vos énumérations, vous devez veiller à éviter les références ambiguës.</span><span class="sxs-lookup"><span data-stu-id="bcd90-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="bcd90-112">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bcd90-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="bcd90-113">En supposant que `Monday` est membre de l' `Days` énumération et de l' `Workdays` énumération, ce code génère une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="bcd90-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="bcd90-114">Pour éviter des références ambiguës quand vous faites référence à une constante individuelle, qualifiez le nom de la constante avec son énumération.</span><span class="sxs-lookup"><span data-stu-id="bcd90-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="bcd90-115">Le code suivant fait référence aux `Saturday` constantes dans les `Days` `WorkDays` énumérations et.</span><span class="sxs-lookup"><span data-stu-id="bcd90-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="bcd90-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcd90-116">See also</span></span>

- [<span data-ttu-id="bcd90-117">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="bcd90-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="bcd90-118">How to: Declare an, énumération</span><span class="sxs-lookup"><span data-stu-id="bcd90-118">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="bcd90-119">Comment : faire référence à un membre d'énumération</span><span class="sxs-lookup"><span data-stu-id="bcd90-119">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="bcd90-120">Comment : itérer au sein d'une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bcd90-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="bcd90-121">Comment : déterminer la chaîne associée à une valeur d'énumération</span><span class="sxs-lookup"><span data-stu-id="bcd90-121">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="bcd90-122">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="bcd90-122">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="bcd90-123">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="bcd90-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="bcd90-124">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="bcd90-124">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="bcd90-125">Imports, instruction (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="bcd90-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="bcd90-126">Data types</span><span class="sxs-lookup"><span data-stu-id="bcd90-126">Data Types</span></span>](../../../language-reference/data-types/index.md)
