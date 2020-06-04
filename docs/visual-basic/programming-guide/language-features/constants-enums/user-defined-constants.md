---
title: Constantes définies par l'utilisateur
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 14f3de39eb8d8e6820e2b40792a8e8e57217e410
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414374"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="2532c-102">Constantes définies par l'utilisateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2532c-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="2532c-103">Une constante est un nom explicite qui prend la place d’un nombre ou d’une chaîne qui ne change pas.</span><span class="sxs-lookup"><span data-stu-id="2532c-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="2532c-104">Les constantes stockent des valeurs qui, comme leur nom l’indique, demeurent constantes tout au long de l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="2532c-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="2532c-105">Vous pouvez utiliser des constantes définies par les contrôles ou les composants avec lesquels vous travaillez, ou vous pouvez créer les vôtres.</span><span class="sxs-lookup"><span data-stu-id="2532c-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="2532c-106">Les constantes que vous créez vous-même sont décrites comme étant *définies par l’utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="2532c-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="2532c-107">Vous déclarez une constante avec l' `Const` instruction, en utilisant les mêmes instructions que pour la création d’un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="2532c-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="2532c-108">Si `Option Strict` est `On` , vous devez déclarer explicitement le type de constante.</span><span class="sxs-lookup"><span data-stu-id="2532c-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="2532c-109">Utilisation de l’instruction Const</span><span class="sxs-lookup"><span data-stu-id="2532c-109">Const Statement Usage</span></span>  
 <span data-ttu-id="2532c-110">Une `Const` instruction peut représenter une quantité mathématique ou de date/heure :</span><span class="sxs-lookup"><span data-stu-id="2532c-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="2532c-111">Il peut également définir des `String` constantes :</span><span class="sxs-lookup"><span data-stu-id="2532c-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="2532c-112">L’expression située à droite du signe égal ( `=` ) est souvent un nombre ou une chaîne littérale, mais il peut également s’agir d’une expression qui produit un nombre ou une chaîne (bien que cette expression ne puisse pas contenir d’appels à des fonctions).</span><span class="sxs-lookup"><span data-stu-id="2532c-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="2532c-113">Vous pouvez même définir des constantes en termes de constantes précédemment définies :</span><span class="sxs-lookup"><span data-stu-id="2532c-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="2532c-114">Étendue des constantes définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="2532c-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="2532c-115">`Const`La portée d’une instruction est identique à celle d’une variable déclarée au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="2532c-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="2532c-116">Vous pouvez spécifier l’étendue de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="2532c-116">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="2532c-117">Pour créer une constante qui existe uniquement dans une procédure, déclarez-la dans cette procédure.</span><span class="sxs-lookup"><span data-stu-id="2532c-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="2532c-118">Pour créer une constante disponible pour toutes les procédures dans une classe, mais pas pour le code situé en dehors de ce module, déclarez-la dans la section déclarations de la classe.</span><span class="sxs-lookup"><span data-stu-id="2532c-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="2532c-119">Pour créer une constante qui est disponible pour tous les membres d’un assembly, mais pas pour les clients externes de l’assembly, déclarez-le à l’aide du `Friend` mot clé dans la section déclarations de la classe.</span><span class="sxs-lookup"><span data-stu-id="2532c-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="2532c-120">Pour créer une constante disponible dans l’ensemble de l’application, déclarez-la à l’aide du `Public` mot clé dans la section déclarations de la classe.</span><span class="sxs-lookup"><span data-stu-id="2532c-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="2532c-121">Pour plus d’informations, consultez [Comment : déclarer une constante](how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="2532c-121">For more information, see [How to: Declare A Constant](how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="2532c-122">Éviter les références circulaires</span><span class="sxs-lookup"><span data-stu-id="2532c-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="2532c-123">Étant donné que les constantes peuvent être définies en termes d’autres constantes, il est possible de créer par inadvertance un *cycle*, ou référence circulaire, entre deux constantes ou plus.</span><span class="sxs-lookup"><span data-stu-id="2532c-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="2532c-124">Un cycle se produit lorsque vous avez au moins deux constantes publiques, chacune d’elles étant définie d’après les autres, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2532c-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="2532c-125">Si un cycle se produit, Visual Basic génère une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="2532c-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2532c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2532c-126">See also</span></span>

- [<span data-ttu-id="2532c-127">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="2532c-127">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="2532c-128">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="2532c-128">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="2532c-129">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="2532c-129">Constants and Enumerations</span></span>](index.md)
- [<span data-ttu-id="2532c-130">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="2532c-130">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="2532c-131">Vue d'ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="2532c-131">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="2532c-132">Vue d'ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="2532c-132">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="2532c-133">How to: Declare an, énumération</span><span class="sxs-lookup"><span data-stu-id="2532c-133">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="2532c-134">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="2532c-134">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="2532c-135">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="2532c-135">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
