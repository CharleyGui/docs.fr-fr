---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 01c441576cb4247933c053f2043296733f99fdeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965421"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="fdbb8-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdbb8-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="fdbb8-103">Spécifie qu’une variable ou une propriété peut être lue mais pas écrite.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdbb8-104">Notes</span><span class="sxs-lookup"><span data-stu-id="fdbb8-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="fdbb8-105">Règles</span><span class="sxs-lookup"><span data-stu-id="fdbb8-105">Rules</span></span>  
  
- <span data-ttu-id="fdbb8-106">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="fdbb8-106">**Declaration Context.**</span></span> <span data-ttu-id="fdbb8-107">Vous pouvez utiliser `ReadOnly` seulement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="fdbb8-108">Cela signifie que le contexte de Déclaration `ReadOnly` pour un élément doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="fdbb8-109">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="fdbb8-109">**Combined Modifiers.**</span></span> <span data-ttu-id="fdbb8-110">Vous ne pouvez `ReadOnly` pas spécifier `Static` avec dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
- <span data-ttu-id="fdbb8-111">**Affectation d’une valeur.**</span><span class="sxs-lookup"><span data-stu-id="fdbb8-111">**Assigning a Value.**</span></span> <span data-ttu-id="fdbb8-112">Le code qui utilise `ReadOnly` une propriété ne peut pas définir sa valeur.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="fdbb8-113">Toutefois, le code qui a accès au stockage sous-jacent peut affecter ou modifier la valeur à tout moment.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="fdbb8-114">Vous pouvez assigner une valeur `ReadOnly` à une variable uniquement dans sa déclaration ou dans le constructeur d’une classe ou d’une structure dans laquelle elle est définie.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="fdbb8-115">Quand utiliser une variable ReadOnly</span><span class="sxs-lookup"><span data-stu-id="fdbb8-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="fdbb8-116">Dans certaines situations, vous ne pouvez pas utiliser une [instruction Const](../../../visual-basic/language-reference/statements/const-statement.md) pour déclarer et assigner une valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="fdbb8-117">Par exemple, l' `Const` instruction peut ne pas accepter le type de données que vous souhaitez affecter, ou vous ne pourrez peut-être pas calculer la valeur au moment de la compilation à l’aide d’une expression constante.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="fdbb8-118">Vous ne connaissez peut-être même pas la valeur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="fdbb8-119">Dans ce cas, vous pouvez utiliser une `ReadOnly` variable pour contenir une valeur constante.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fdbb8-120">Si le type de données de la variable est un type référence, tel qu’un tableau ou une instance de classe, ses membres peuvent être modifiés même si la variable `ReadOnly`elle-même est.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="fdbb8-121">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="fdbb8-122">En cas d’initialisation, le tableau désigné par `characterArray()` contient «x», «y» et «z».</span><span class="sxs-lookup"><span data-stu-id="fdbb8-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="fdbb8-123">Étant donné que `characterArray` la `ReadOnly`variable est, vous ne pouvez pas modifier sa valeur une fois qu’elle est initialisée; autrement dit, vous ne pouvez pas lui assigner un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="fdbb8-124">Toutefois, vous pouvez modifier les valeurs d’un ou plusieurs membres du tableau.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="fdbb8-125">Suite à un appel à la `changeArrayElement`procédure, le tableau désigné par `characterArray()` contient «x», «M» et «z».</span><span class="sxs-lookup"><span data-stu-id="fdbb8-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="fdbb8-126">Notez que cela est semblable à la déclaration d’un paramètre de procédure à [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), ce qui empêche la procédure de modifier l’argument appelant lui-même, mais lui permet de modifier ses membres.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdbb8-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="fdbb8-127">Example</span></span>  
 <span data-ttu-id="fdbb8-128">L’exemple suivant définit une `ReadOnly` propriété pour la date de l’embauche d’un employé.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="fdbb8-129">La classe stocke la valeur de propriété en interne `Private` en tant que variable, et seul le code à l’intérieur de la classe peut changer cette valeur.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="fdbb8-130">Toutefois, la propriété est `Public`, et tout code qui peut accéder à la classe peut lire la propriété.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="fdbb8-131">Le modificateur `ReadOnly` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="fdbb8-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="fdbb8-132">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="fdbb8-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="fdbb8-133">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="fdbb8-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="fdbb8-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdbb8-134">See also</span></span>

- [<span data-ttu-id="fdbb8-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="fdbb8-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="fdbb8-136">Mots clés</span><span class="sxs-lookup"><span data-stu-id="fdbb8-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
