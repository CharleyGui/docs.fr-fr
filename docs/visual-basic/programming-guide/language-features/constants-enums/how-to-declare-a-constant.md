---
title: 'Comment : déclarer une constante'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 5054d4a4fc02d8bd22efceb01770fc54167d8cb3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347473"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="4bb84-102">Comment : déclarer une constante (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bb84-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="4bb84-103">You use the `Const` statement to declare a constant and set its value.</span><span class="sxs-lookup"><span data-stu-id="4bb84-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="4bb84-104">By declaring a constant, you assign a meaningful name to a value.</span><span class="sxs-lookup"><span data-stu-id="4bb84-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="4bb84-105">Once a constant is declared, it cannot be modified or assigned a new value.</span><span class="sxs-lookup"><span data-stu-id="4bb84-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="4bb84-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="4bb84-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="4bb84-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span><span class="sxs-lookup"><span data-stu-id="4bb84-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="4bb84-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span><span class="sxs-lookup"><span data-stu-id="4bb84-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="4bb84-109">To declare a constant</span><span class="sxs-lookup"><span data-stu-id="4bb84-109">To declare a constant</span></span>  
  
- <span data-ttu-id="4bb84-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span><span class="sxs-lookup"><span data-stu-id="4bb84-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="4bb84-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span><span class="sxs-lookup"><span data-stu-id="4bb84-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="4bb84-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span><span class="sxs-lookup"><span data-stu-id="4bb84-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="4bb84-113">The compiler determines the type of the constant from the type of the expression.</span><span class="sxs-lookup"><span data-stu-id="4bb84-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="4bb84-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="4bb84-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="4bb84-115">To declare a constant that has an explicitly stated data type</span><span class="sxs-lookup"><span data-stu-id="4bb84-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="4bb84-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span><span class="sxs-lookup"><span data-stu-id="4bb84-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="4bb84-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span><span class="sxs-lookup"><span data-stu-id="4bb84-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="4bb84-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="4bb84-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="4bb84-119">To declare multiple constants on a single line</span><span class="sxs-lookup"><span data-stu-id="4bb84-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="4bb84-120">Separate the declarations with a comma and a space, as in the following example:</span><span class="sxs-lookup"><span data-stu-id="4bb84-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4bb84-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bb84-121">See also</span></span>

- [<span data-ttu-id="4bb84-122">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="4bb84-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="4bb84-123">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="4bb84-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="4bb84-124">Vue d’ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="4bb84-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="4bb84-125">Guide pratique : déclarer une constante</span><span class="sxs-lookup"><span data-stu-id="4bb84-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="4bb84-126">Constantes définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="4bb84-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="4bb84-127">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="4bb84-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="4bb84-128">Guide pratique : regrouper les valeurs de constante connexes</span><span class="sxs-lookup"><span data-stu-id="4bb84-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="4bb84-129">Vue d’ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="4bb84-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="4bb84-130">Guide pratique : déclarer des énumérations</span><span class="sxs-lookup"><span data-stu-id="4bb84-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="4bb84-131">Guide pratique : faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="4bb84-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="4bb84-132">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="4bb84-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="4bb84-133">Guide pratique : itérer au sein d’une énumération</span><span class="sxs-lookup"><span data-stu-id="4bb84-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="4bb84-134">Guide pratique : déterminer la chaîne associée à une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="4bb84-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="4bb84-135">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="4bb84-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="4bb84-136">Vue d’ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="4bb84-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="4bb84-137">Vue d’ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="4bb84-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="4bb84-138">How to: Declare an Enumeration</span><span class="sxs-lookup"><span data-stu-id="4bb84-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="4bb84-139">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="4bb84-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="4bb84-140">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="4bb84-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="4bb84-141">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="4bb84-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
