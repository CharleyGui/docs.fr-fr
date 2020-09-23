---
title: 'Comment : modifier la valeur d’un argument de la procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: 9960dacc053c5dc8d8cfdfd6eaa0ea3258ed0fea
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077070"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="654f9-102">Comment : modifier la valeur d'un argument de la procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="654f9-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>

<span data-ttu-id="654f9-103">Lorsque vous appelez une procédure, chaque argument que vous fournissez correspond à l’un des paramètres définis dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="654f9-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="654f9-104">Dans certains cas, le code de la procédure peut modifier la valeur sous-jacente d’un argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="654f9-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="654f9-105">Dans d’autres cas, la procédure ne peut modifier que la copie locale d’un argument.</span><span class="sxs-lookup"><span data-stu-id="654f9-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="654f9-106">Quand vous appelez la procédure, Visual Basic effectue une copie locale de chaque argument qui est passé en [ByVal](../../../language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="654f9-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="654f9-107">Pour chaque argument passé [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic donne au code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="654f9-107">For each argument passed [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="654f9-108">Si l’élément sous-jacent dans le code appelant est un élément modifiable et que l’argument est passé `ByRef` , le code de la procédure peut utiliser la référence directe pour modifier la valeur de l’élément dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="654f9-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="654f9-109">Modification de la valeur sous-jacente</span><span class="sxs-lookup"><span data-stu-id="654f9-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="654f9-110">Pour modifier la valeur sous-jacente d’un argument de procédure dans le code appelant</span><span class="sxs-lookup"><span data-stu-id="654f9-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="654f9-111">Dans la déclaration de procédure, spécifiez [ByRef](../../../language-reference/modifiers/byref.md) pour le paramètre correspondant à l’argument.</span><span class="sxs-lookup"><span data-stu-id="654f9-111">In the procedure declaration, specify [ByRef](../../../language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="654f9-112">Dans le code appelant, passer un élément de programmation modifiable comme argument.</span><span class="sxs-lookup"><span data-stu-id="654f9-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="654f9-113">Dans le code appelant, ne placez pas l’argument entre parenthèses dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="654f9-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="654f9-114">Dans le code de la procédure, utilisez le nom du paramètre pour assigner une valeur à l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="654f9-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="654f9-115">Pour une démonstration, reportez-vous à l’exemple.</span><span class="sxs-lookup"><span data-stu-id="654f9-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="654f9-116">Modification des copies locales</span><span class="sxs-lookup"><span data-stu-id="654f9-116">Changing Local Copies</span></span>  

 <span data-ttu-id="654f9-117">Si l’élément sous-jacent dans le code appelant est un élément non modifiable, ou si l’argument est passé `ByVal` , la procédure ne peut pas modifier sa valeur dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="654f9-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="654f9-118">Toutefois, la procédure peut modifier sa copie locale d’un tel argument.</span><span class="sxs-lookup"><span data-stu-id="654f9-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="654f9-119">Pour modifier la copie d’un argument de procédure dans le code de la procédure</span><span class="sxs-lookup"><span data-stu-id="654f9-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="654f9-120">Dans la déclaration de procédure, spécifiez [ByVal](../../../language-reference/modifiers/byval.md) pour le paramètre correspondant à l’argument.</span><span class="sxs-lookup"><span data-stu-id="654f9-120">In the procedure declaration, specify [ByVal](../../../language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="654f9-121">- ou -</span><span class="sxs-lookup"><span data-stu-id="654f9-121">-or-</span></span>  
  
     <span data-ttu-id="654f9-122">Dans le code appelant, mettez l’argument entre parenthèses dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="654f9-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="654f9-123">Cela oblige Visual Basic à passer l’argument par valeur, même si le paramètre correspondant spécifie `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="654f9-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="654f9-124">Dans le code de la procédure, utilisez le nom du paramètre pour assigner une valeur à la copie locale de l’argument.</span><span class="sxs-lookup"><span data-stu-id="654f9-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="654f9-125">La valeur sous-jacente dans le code appelant n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="654f9-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="654f9-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="654f9-126">Example</span></span>  

 <span data-ttu-id="654f9-127">L’exemple suivant montre deux procédures qui prennent une variable tableau et opèrent sur ses éléments.</span><span class="sxs-lookup"><span data-stu-id="654f9-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="654f9-128">La `increase` procédure ajoute simplement une à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="654f9-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="654f9-129">La `replace` procédure assigne un nouveau tableau au paramètre `a()` , puis ajoute un à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="654f9-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="654f9-130">Le premier `MsgBox` appel affiche « après l’augmentation (n) : 11, 21, 31, 41 ».</span><span class="sxs-lookup"><span data-stu-id="654f9-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="654f9-131">Étant donné que le tableau `n` est un type référence, `replace` peut modifier ses membres, même si le mécanisme de passage est `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="654f9-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="654f9-132">Le deuxième `MsgBox` appel affiche « after Replace (n) : 101, 201, 301 ».</span><span class="sxs-lookup"><span data-stu-id="654f9-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="654f9-133">Étant donné que `n` est passé `ByRef` , `replace` peut modifier la variable `n` dans le code appelant et lui assigner un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="654f9-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="654f9-134">Étant donné que `n` est un type référence, `replace` peut également modifier ses membres.</span><span class="sxs-lookup"><span data-stu-id="654f9-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="654f9-135">Vous pouvez empêcher la procédure de modifier la variable elle-même dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="654f9-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="654f9-136">Consultez [Comment : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="654f9-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="654f9-137">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="654f9-137">Compile the code</span></span>  

 <span data-ttu-id="654f9-138">Lorsque vous transmettez une variable par référence, vous devez utiliser le `ByRef` mot clé pour spécifier ce mécanisme.</span><span class="sxs-lookup"><span data-stu-id="654f9-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="654f9-139">La valeur par défaut de Visual Basic consiste à passer des arguments par valeur.</span><span class="sxs-lookup"><span data-stu-id="654f9-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="654f9-140">Toutefois, il est recommandé d’inclure le mot clé [ByVal](../../../language-reference/modifiers/byval.md) ou [ByRef](../../../language-reference/modifiers/byref.md) avec chaque paramètre déclaré.</span><span class="sxs-lookup"><span data-stu-id="654f9-140">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="654f9-141">Cela rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="654f9-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="654f9-142">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="654f9-142">.NET Framework Security</span></span>  

 <span data-ttu-id="654f9-143">Il existe toujours un risque potentiel d’autoriser une procédure à modifier la valeur sous-jacente d’un argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="654f9-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="654f9-144">Veillez à ce que cette valeur soit modifiée et soyez prêt à vérifier sa validité avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="654f9-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654f9-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="654f9-145">See also</span></span>

- [<span data-ttu-id="654f9-146">Procédures</span><span class="sxs-lookup"><span data-stu-id="654f9-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="654f9-147">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="654f9-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="654f9-148">Comment : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="654f9-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="654f9-149">Passage des arguments par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="654f9-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="654f9-150">Différences entre les arguments modifiables et non modifiables</span><span class="sxs-lookup"><span data-stu-id="654f9-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="654f9-151">Différences entre le passage d'un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="654f9-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="654f9-152">Comment : protéger un argument de procédure contre les modifications de valeur</span><span class="sxs-lookup"><span data-stu-id="654f9-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="654f9-153">Comment : forcer le passage d'un argument par valeur</span><span class="sxs-lookup"><span data-stu-id="654f9-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="654f9-154">Passage des arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="654f9-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="654f9-155">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="654f9-155">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
