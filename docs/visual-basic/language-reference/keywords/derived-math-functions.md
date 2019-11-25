---
title: Fonctions mathématiques dérivées
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: 73cf56dd72f2baac0474d6f5c4e88228a1fe38cf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349849"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="774a8-102">Fonctions mathématiques dérivées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="774a8-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="774a8-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span><span class="sxs-lookup"><span data-stu-id="774a8-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="774a8-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span><span class="sxs-lookup"><span data-stu-id="774a8-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="774a8-105">Fonction</span><span class="sxs-lookup"><span data-stu-id="774a8-105">Function</span></span>|<span data-ttu-id="774a8-106">Derived equivalents</span><span class="sxs-lookup"><span data-stu-id="774a8-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="774a8-107">Secant (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-107">Secant (Sec(x))</span></span>|<span data-ttu-id="774a8-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="774a8-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="774a8-109">Cosecant (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="774a8-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="774a8-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="774a8-111">Cotangent (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="774a8-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="774a8-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="774a8-113">Inverse sine (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="774a8-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="774a8-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="774a8-115">Inverse cosine (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="774a8-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="774a8-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="774a8-117">Inverse secant (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="774a8-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="774a8-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="774a8-119">Inverse cosecant (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="774a8-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="774a8-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="774a8-121">Inverse cotangent (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="774a8-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="774a8-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="774a8-123">Hyperbolic sine (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="774a8-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="774a8-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="774a8-125">Hyperbolic cosine (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="774a8-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="774a8-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="774a8-127">Hyperbolic tangent (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="774a8-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="774a8-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="774a8-129">Hyperbolic secant (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="774a8-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="774a8-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="774a8-131">Hyperbolic cosecant (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="774a8-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="774a8-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="774a8-133">Hyperbolic cotangent (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="774a8-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="774a8-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="774a8-135">Inverse hyperbolic sine (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="774a8-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="774a8-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="774a8-137">Inverse hyperbolic cosine (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="774a8-138">Log(x + Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="774a8-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="774a8-139">Inverse hyperbolic tangent (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="774a8-140">Log((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="774a8-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="774a8-141">Inverse hyperbolic secant (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="774a8-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="774a8-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="774a8-143">Inverse hyperbolic cosecant (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="774a8-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="774a8-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="774a8-145">Inverse hyperbolic cotangent (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="774a8-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="774a8-146">Log((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="774a8-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="774a8-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="774a8-147">See also</span></span>

- [<span data-ttu-id="774a8-148">Fonctions mathématiques</span><span class="sxs-lookup"><span data-stu-id="774a8-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
