---
title: Différences entre les arguments modifiables et non modifiables
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 989795ee2cdd3a78b71bad4d95cf9b384c2719bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341389"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="1b07a-102">Différences entre les arguments modifiables et non modifiables (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b07a-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="1b07a-103">Lorsque vous appelez une procédure, vous lui transmettez généralement un ou plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="1b07a-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="1b07a-104">Chaque argument correspond à un élément de programmation sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="1b07a-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="1b07a-105">Les éléments sous-jacents et les arguments peuvent eux-mêmes être modifiables ou non modifiables.</span><span class="sxs-lookup"><span data-stu-id="1b07a-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="1b07a-106">Éléments modifiables et non modifiables</span><span class="sxs-lookup"><span data-stu-id="1b07a-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="1b07a-107">Un élément de programmation peut être un *élément modifiable*, dont la valeur peut être modifiée ou un *élément non modifiable*, qui a une valeur fixe une fois qu’il a été créé.</span><span class="sxs-lookup"><span data-stu-id="1b07a-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="1b07a-108">Le tableau suivant répertorie les éléments de programmation modifiables et non modifiables.</span><span class="sxs-lookup"><span data-stu-id="1b07a-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="1b07a-109">Éléments modifiables</span><span class="sxs-lookup"><span data-stu-id="1b07a-109">Modifiable elements</span></span>|<span data-ttu-id="1b07a-110">Éléments non modifiables</span><span class="sxs-lookup"><span data-stu-id="1b07a-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="1b07a-111">Variables locales (déclarées dans les procédures), y compris les variables objets, à l’exception de en lecture seule</span><span class="sxs-lookup"><span data-stu-id="1b07a-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="1b07a-112">Variables, champs et propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="1b07a-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="1b07a-113">Champs (variables de membre de modules, classes et structures), à l’exception de en lecture seule</span><span class="sxs-lookup"><span data-stu-id="1b07a-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="1b07a-114">Constantes et littéraux</span><span class="sxs-lookup"><span data-stu-id="1b07a-114">Constants and literals</span></span>|  
|<span data-ttu-id="1b07a-115">Propriétés, à l’exception de lecture seule</span><span class="sxs-lookup"><span data-stu-id="1b07a-115">Properties, except for read-only</span></span>|<span data-ttu-id="1b07a-116">Membres de l’énumération</span><span class="sxs-lookup"><span data-stu-id="1b07a-116">Enumeration members</span></span>|  
|<span data-ttu-id="1b07a-117">Éléments de tableau</span><span class="sxs-lookup"><span data-stu-id="1b07a-117">Array elements</span></span>|<span data-ttu-id="1b07a-118">Expressions (même si leurs éléments sont modifiables)</span><span class="sxs-lookup"><span data-stu-id="1b07a-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="1b07a-119">Arguments modifiables et non modifiables</span><span class="sxs-lookup"><span data-stu-id="1b07a-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="1b07a-120">Un *argument modifiable* est un argument avec un élément sous-jacent modifiable.</span><span class="sxs-lookup"><span data-stu-id="1b07a-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="1b07a-121">Le code appelant peut stocker une nouvelle valeur à tout moment, et si vous transmettez l’argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), le code de la procédure peut également modifier l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="1b07a-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="1b07a-122">Un *argument non modifiable* a un élément sous-jacent non modifiable ou est passé avec la valeur [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="1b07a-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="1b07a-123">La procédure ne peut pas modifier l’élément sous-jacent dans le code appelant, même s’il s’agit d’un élément modifiable.</span><span class="sxs-lookup"><span data-stu-id="1b07a-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="1b07a-124">S’il s’agit d’un élément non modifiable, le code appelant lui-même ne peut pas le modifier.</span><span class="sxs-lookup"><span data-stu-id="1b07a-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="1b07a-125">La procédure appelée peut modifier sa copie locale d’un argument non modifiable, mais cette modification n’affecte pas l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="1b07a-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b07a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b07a-126">See also</span></span>

- [<span data-ttu-id="1b07a-127">Procédures</span><span class="sxs-lookup"><span data-stu-id="1b07a-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1b07a-128">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="1b07a-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1b07a-129">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="1b07a-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="1b07a-130">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="1b07a-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="1b07a-131">Différences entre le passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="1b07a-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="1b07a-132">Guide pratique : modifier la valeur d’un argument de la procédure</span><span class="sxs-lookup"><span data-stu-id="1b07a-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="1b07a-133">Guide pratique : protéger un argument de procédure contre les modifications de valeur</span><span class="sxs-lookup"><span data-stu-id="1b07a-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="1b07a-134">Guide pratique : forcer le passage d’un argument par valeur</span><span class="sxs-lookup"><span data-stu-id="1b07a-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="1b07a-135">Passage des arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="1b07a-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="1b07a-136">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="1b07a-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
