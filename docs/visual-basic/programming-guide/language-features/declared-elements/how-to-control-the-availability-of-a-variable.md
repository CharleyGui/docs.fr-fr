---
title: "Comment : contrôler la disponibilité d'une variable"
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 886b57909cf6ba25dbaceea5c5f06eb4e3ba6f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345392"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="c691c-102">Comment : contrôler la disponibilité d'une variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c691c-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="c691c-103">Vous contrôlez la disponibilité d’une variable en spécifiant son *niveau d’accès*.</span><span class="sxs-lookup"><span data-stu-id="c691c-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="c691c-104">Le niveau d’accès détermine le code qui a l’autorisation de lire ou d’écrire dans la variable.</span><span class="sxs-lookup"><span data-stu-id="c691c-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="c691c-105">Les *variables membres* (définies au niveau du module et en dehors de toute procédure) sont par défaut accessibles au public, ce qui signifie que tout code qui peut les voir peut y accéder.</span><span class="sxs-lookup"><span data-stu-id="c691c-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="c691c-106">Vous pouvez modifier ce paramétrage en spécifiant un modificateur d’accès.</span><span class="sxs-lookup"><span data-stu-id="c691c-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="c691c-107">Les *variables locales* (définies à l’intérieur d’une procédure) ont un accès public, bien que seul le code au sein de leur procédure puisse y accéder.</span><span class="sxs-lookup"><span data-stu-id="c691c-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="c691c-108">Vous ne pouvez pas modifier le niveau d’accès d’une variable locale, mais vous pouvez modifier le niveau d’accès de la procédure qui la contient.</span><span class="sxs-lookup"><span data-stu-id="c691c-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="c691c-109">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c691c-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="c691c-110">Accès privé et public</span><span class="sxs-lookup"><span data-stu-id="c691c-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="c691c-111">Pour rendre une variable accessible uniquement à partir de son module, de sa classe ou de sa structure</span><span class="sxs-lookup"><span data-stu-id="c691c-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="c691c-112">Placez l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour la variable à l’intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="c691c-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="c691c-113">Incluez le mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md) dans l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="c691c-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c691c-114">Vous pouvez lire ou écrire dans la variable à partir de n’importe quel endroit dans le module, la classe ou la structure, mais pas en dehors de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="c691c-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="c691c-115">Pour rendre une variable accessible à partir de n’importe quel code qui peut la voir</span><span class="sxs-lookup"><span data-stu-id="c691c-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="c691c-116">Pour une variable membre, placez l’instruction `Dim` pour la variable à l’intérieur d’un module, d’une classe ou d’une structure, mais en dehors d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="c691c-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="c691c-117">Incluez le mot clé [public](../../../../visual-basic/language-reference/modifiers/public.md) dans l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="c691c-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c691c-118">Vous pouvez lire ou écrire dans la variable à partir de n’importe quel code qui interagit avec votre assembly.</span><span class="sxs-lookup"><span data-stu-id="c691c-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="c691c-119">-ou-</span><span class="sxs-lookup"><span data-stu-id="c691c-119">-or-</span></span>  
  
1. <span data-ttu-id="c691c-120">Pour une variable locale, placez l’instruction `Dim` pour la variable à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="c691c-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="c691c-121">N’incluez pas le mot clé `Public` dans l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="c691c-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c691c-122">Vous pouvez lire ou écrire dans la variable à n’importe quel endroit de la procédure, mais pas en dehors de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="c691c-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="c691c-123">Accès protégé et ami</span><span class="sxs-lookup"><span data-stu-id="c691c-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="c691c-124">Vous pouvez limiter le niveau d’accès d’une variable à sa classe et à ses classes dérivées, ou à son assembly.</span><span class="sxs-lookup"><span data-stu-id="c691c-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="c691c-125">Vous pouvez également spécifier l’Union de ces limitations, qui autorise l’accès à partir du code dans toute classe dérivée ou à tout autre emplacement dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="c691c-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="c691c-126">Vous spécifiez cette Union en combinant les mots clés `Protected` et `Friend` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="c691c-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="c691c-127">Pour rendre une variable accessible uniquement à partir de sa classe et de toutes les classes dérivées</span><span class="sxs-lookup"><span data-stu-id="c691c-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="c691c-128">Placez l’instruction `Dim` pour la variable à l’intérieur d’une classe, mais en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="c691c-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="c691c-129">Incluez le mot clé [protected](../../../../visual-basic/language-reference/modifiers/protected.md) dans l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="c691c-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c691c-130">Vous pouvez lire ou écrire dans la variable à n’importe quel endroit de la classe, ainsi qu’à partir d’une classe dérivée de celle-ci, mais pas de l’extérieur d’une classe de la chaîne de dérivation.</span><span class="sxs-lookup"><span data-stu-id="c691c-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="c691c-131">Pour rendre une variable accessible uniquement à partir du même assembly</span><span class="sxs-lookup"><span data-stu-id="c691c-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="c691c-132">Placez l’instruction `Dim` pour la variable à l’intérieur d’un module, d’une classe ou d’une structure, mais en dehors d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="c691c-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="c691c-133">Incluez le mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) dans l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="c691c-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c691c-134">Vous pouvez lire ou écrire dans la variable depuis n’importe quel endroit du module, de la classe ou de la structure, ainsi que depuis n’importe quel code dans le même assembly, mais pas à l’extérieur de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c691c-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c691c-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="c691c-135">Example</span></span>  
 <span data-ttu-id="c691c-136">L’exemple suivant montre des déclarations de variables avec des niveaux d’accès `Public`, `Protected`, `Friend`, `Protected Friend`et `Private`.</span><span class="sxs-lookup"><span data-stu-id="c691c-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="c691c-137">Notez que lorsque l’instruction `Dim` spécifie un niveau d’accès, vous n’avez pas besoin d’inclure le mot clé `Dim`.</span><span class="sxs-lookup"><span data-stu-id="c691c-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="c691c-138">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c691c-138">.NET Framework Security</span></span>  
 <span data-ttu-id="c691c-139">Plus le niveau d’accès d’une variable est restrictif, plus les risques de mauvaise utilisation du code malveillant sont faibles.</span><span class="sxs-lookup"><span data-stu-id="c691c-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c691c-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c691c-140">See also</span></span>

- [<span data-ttu-id="c691c-141">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c691c-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c691c-142">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="c691c-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="c691c-143">Public</span><span class="sxs-lookup"><span data-stu-id="c691c-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="c691c-144">Protected</span><span class="sxs-lookup"><span data-stu-id="c691c-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="c691c-145">Friend</span><span class="sxs-lookup"><span data-stu-id="c691c-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="c691c-146">Private</span><span class="sxs-lookup"><span data-stu-id="c691c-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
