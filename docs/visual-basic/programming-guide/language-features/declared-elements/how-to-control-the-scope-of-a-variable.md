---
title: "Comment : contrôler la portée d'une variable (Visual Basic)"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 23a10bd2d6c0c9f3a13bff864559460c48927e01
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582598"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="406c9-102">Comment : contrôler la portée d'une variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="406c9-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="406c9-103">Normalement, une variable est dans la *portée*, ou visible à des fins de référence, dans toute la région dans laquelle vous la déclarez.</span><span class="sxs-lookup"><span data-stu-id="406c9-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="406c9-104">Dans certains cas, le niveau d' *accès* de la variable peut influencer son étendue.</span><span class="sxs-lookup"><span data-stu-id="406c9-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="406c9-105">Pour plus d'informations, consultez [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="406c9-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="406c9-106">Portée au niveau du bloc ou de la procédure</span><span class="sxs-lookup"><span data-stu-id="406c9-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="406c9-107">Pour rendre une variable visible uniquement dans un bloc</span><span class="sxs-lookup"><span data-stu-id="406c9-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="406c9-108">Placez l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour la variable entre les instructions de déclaration de début et de fin de ce bloc, par exemple entre les instructions `For` et `Next` d’une boucle `For`.</span><span class="sxs-lookup"><span data-stu-id="406c9-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="406c9-109">Vous ne pouvez faire référence à la variable qu’à partir du bloc.</span><span class="sxs-lookup"><span data-stu-id="406c9-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="406c9-110">Pour rendre une variable visible uniquement dans une procédure</span><span class="sxs-lookup"><span data-stu-id="406c9-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="406c9-111">Placez l’instruction `Dim` pour la variable à l’intérieur de la procédure, mais en dehors de tout bloc (par exemple, un bloc `With`... `End With`).</span><span class="sxs-lookup"><span data-stu-id="406c9-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="406c9-112">Vous ne pouvez faire référence à la variable qu’à partir de la procédure, y compris à l’intérieur de n’importe quel bloc contenu dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="406c9-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="406c9-113">Portée au niveau du module ou de l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="406c9-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="406c9-114">Pour plus de commodité, le *niveau de module* à simple terme s’applique de la même manière aux modules, aux classes et aux structures.</span><span class="sxs-lookup"><span data-stu-id="406c9-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="406c9-115">Le niveau d’accès d’une variable de niveau module détermine sa portée.</span><span class="sxs-lookup"><span data-stu-id="406c9-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="406c9-116">L’espace de noms qui contient le module, la classe ou la structure influence également la portée.</span><span class="sxs-lookup"><span data-stu-id="406c9-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="406c9-117">Pour rendre une variable visible dans l’ensemble d’un module, d’une classe ou d’une structure</span><span class="sxs-lookup"><span data-stu-id="406c9-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="406c9-118">Placez l’instruction `Dim` pour la variable à l’intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="406c9-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="406c9-119">Incluez le mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md) dans l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="406c9-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="406c9-120">Vous pouvez faire référence à la variable depuis n’importe quel endroit du module, de la classe ou de la structure, mais pas à l’extérieur.</span><span class="sxs-lookup"><span data-stu-id="406c9-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="406c9-121">Pour rendre une variable visible dans l’ensemble d’un espace de noms</span><span class="sxs-lookup"><span data-stu-id="406c9-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="406c9-122">Placez l’instruction `Dim` pour la variable à l’intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="406c9-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="406c9-123">Incluez le mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [public](../../../../visual-basic/language-reference/modifiers/public.md) dans l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="406c9-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="406c9-124">Vous pouvez faire référence à la variable depuis n’importe quel emplacement de l’espace de noms contenant le module, la classe ou la structure.</span><span class="sxs-lookup"><span data-stu-id="406c9-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="406c9-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="406c9-125">Example</span></span>  
 <span data-ttu-id="406c9-126">L’exemple suivant déclare une variable au niveau du module et limite sa visibilité au code dans le module.</span><span class="sxs-lookup"><span data-stu-id="406c9-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="406c9-127">Dans l’exemple précédent, toutes les procédures définies dans le module `demonstrateScope` peuvent faire référence à la variable `String` `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="406c9-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="406c9-128">Lorsque la procédure `usePrivateVariable` est appelée, elle affiche le contenu de la variable de chaîne `strMsg` dans une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="406c9-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="406c9-129">Avec la modification suivante apporte à l’exemple précédent, la variable de chaîne `strMsg` peut être référencée par du code n’importe où dans l’espace de noms de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="406c9-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="406c9-130">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="406c9-130">Robust Programming</span></span>  
 <span data-ttu-id="406c9-131">Plus la portée d’une variable est restreinte, moins vous avez d’opportunités pour y faire référence par mégarde à la place d’une autre variable portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="406c9-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="406c9-132">Vous pouvez également réduire les problèmes de correspondance de référence.</span><span class="sxs-lookup"><span data-stu-id="406c9-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="406c9-133">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="406c9-133">.NET Framework Security</span></span>  
 <span data-ttu-id="406c9-134">Plus la portée d’une variable est restreinte, plus les probabilités de code malveillant peuvent être utilisées de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="406c9-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406c9-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="406c9-135">See also</span></span>

- [<span data-ttu-id="406c9-136">Étendue dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="406c9-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="406c9-137">Durée de vie dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="406c9-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="406c9-138">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="406c9-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="406c9-139">Variables</span><span class="sxs-lookup"><span data-stu-id="406c9-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="406c9-140">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="406c9-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="406c9-141">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="406c9-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
