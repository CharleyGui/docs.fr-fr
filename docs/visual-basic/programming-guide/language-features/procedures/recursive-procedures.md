---
title: Procédures récursives
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 646d4e29ed7a0b6367d4b35a7f8641bcf659e616
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352554"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="21eeb-102">Procédures récursives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21eeb-102">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="21eeb-103">Une procédure *récursive* est une procédure qui s’appelle elle-même.</span><span class="sxs-lookup"><span data-stu-id="21eeb-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="21eeb-104">En général, il ne s’agit pas de la méthode la plus efficace pour écrire du code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="21eeb-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="21eeb-105">La procédure suivante utilise la récursivité pour calculer la factorielle de son argument d’origine.</span><span class="sxs-lookup"><span data-stu-id="21eeb-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="21eeb-106">Considérations relatives aux procédures récursives</span><span class="sxs-lookup"><span data-stu-id="21eeb-106">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="21eeb-107">**Limitation des conditions**.</span><span class="sxs-lookup"><span data-stu-id="21eeb-107">**Limiting Conditions**.</span></span> <span data-ttu-id="21eeb-108">Vous devez concevoir une procédure récursive pour tester au moins une condition qui peut mettre fin à la récursivité, et vous devez également gérer le cas où aucune condition n’est satisfaite dans un nombre raisonnable d’appels récursifs.</span><span class="sxs-lookup"><span data-stu-id="21eeb-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="21eeb-109">Si au moins une condition peut être remplie sans échouer, votre procédure exécute un risque élevé d’exécution dans une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="21eeb-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="21eeb-110">**Utilisation de la mémoire**.</span><span class="sxs-lookup"><span data-stu-id="21eeb-110">**Memory Usage**.</span></span> <span data-ttu-id="21eeb-111">Votre application dispose d’une quantité limitée d’espace pour les variables locales.</span><span class="sxs-lookup"><span data-stu-id="21eeb-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="21eeb-112">Chaque fois qu’une procédure s’appelle elle-même, elle utilise plus d’espace pour les copies supplémentaires de ses variables locales.</span><span class="sxs-lookup"><span data-stu-id="21eeb-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="21eeb-113">Si ce processus se poursuit indéfiniment, il finit par provoquer une erreur de <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="21eeb-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="21eeb-114">**Efficacité**.</span><span class="sxs-lookup"><span data-stu-id="21eeb-114">**Efficiency**.</span></span> <span data-ttu-id="21eeb-115">Vous pouvez presque toujours substituer une boucle pour la récursivité.</span><span class="sxs-lookup"><span data-stu-id="21eeb-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="21eeb-116">Une boucle n’a pas la surcharge liée au passage des arguments, à l’initialisation d’un stockage supplémentaire et au retour de valeurs.</span><span class="sxs-lookup"><span data-stu-id="21eeb-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="21eeb-117">Vos performances peuvent être nettement meilleures sans appels récursifs.</span><span class="sxs-lookup"><span data-stu-id="21eeb-117">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="21eeb-118">**Récurrence mutuelle**.</span><span class="sxs-lookup"><span data-stu-id="21eeb-118">**Mutual Recursion**.</span></span> <span data-ttu-id="21eeb-119">Vous pouvez observer des performances très médiocres, voire une boucle infinie, si deux procédures s’appellent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="21eeb-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="21eeb-120">Une telle conception présente les mêmes problèmes qu’une seule procédure récursive, mais peut être plus difficile à détecter et à déboguer.</span><span class="sxs-lookup"><span data-stu-id="21eeb-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="21eeb-121">**Appel avec des parenthèses**.</span><span class="sxs-lookup"><span data-stu-id="21eeb-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="21eeb-122">Quand une procédure `Function` s’appelle elle-même de manière récursive, vous devez faire suivre le nom de la procédure de parenthèses, même s’il n’y a pas de liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="21eeb-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="21eeb-123">Dans le cas contraire, le nom de la fonction est considéré comme représentant la valeur de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="21eeb-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="21eeb-124">**Test**.</span><span class="sxs-lookup"><span data-stu-id="21eeb-124">**Testing**.</span></span> <span data-ttu-id="21eeb-125">Si vous écrivez une procédure récursive, vous devez la tester très attentivement pour vous assurer qu’elle répond toujours à certaines conditions de limitation.</span><span class="sxs-lookup"><span data-stu-id="21eeb-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="21eeb-126">Vous devez également vous assurer que vous ne pouvez pas manquer de mémoire en raison d’un trop grand nombre d’appels récursifs.</span><span class="sxs-lookup"><span data-stu-id="21eeb-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="21eeb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21eeb-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="21eeb-128">Procédures</span><span class="sxs-lookup"><span data-stu-id="21eeb-128">Procedures</span></span>](index.md)
- [<span data-ttu-id="21eeb-129">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="21eeb-129">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="21eeb-130">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="21eeb-130">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="21eeb-131">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="21eeb-131">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="21eeb-132">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="21eeb-132">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="21eeb-133">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="21eeb-133">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="21eeb-134">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="21eeb-134">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="21eeb-135">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="21eeb-135">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="21eeb-136">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="21eeb-136">Loop Structures</span></span>](../control-flow/loop-structures.md)
