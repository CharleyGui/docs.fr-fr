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
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="b31fd-102">Fonctions mathématiques dérivées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b31fd-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="b31fd-103">Le tableau suivant répertorie les fonctions mathématiques non intrinsèques qui peuvent être dérivées des fonctions mathématiques intrinsèques de l’objet <xref:System.Math?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b31fd-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="b31fd-104">Vous pouvez accéder aux fonctions mathématiques intrinsèques en ajoutant des `Imports System.Math` à votre fichier ou projet.</span><span class="sxs-lookup"><span data-stu-id="b31fd-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="b31fd-105">Fonction</span><span class="sxs-lookup"><span data-stu-id="b31fd-105">Function</span></span>|<span data-ttu-id="b31fd-106">Équivalents dérivés</span><span class="sxs-lookup"><span data-stu-id="b31fd-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="b31fd-107">Sécante (sec (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-107">Secant (Sec(x))</span></span>|<span data-ttu-id="b31fd-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="b31fd-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="b31fd-109">Cosécante (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="b31fd-110">1/Sin (x)</span><span class="sxs-lookup"><span data-stu-id="b31fd-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="b31fd-111">Cotangente (CTAN (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="b31fd-112">1/Tan (x)</span><span class="sxs-lookup"><span data-stu-id="b31fd-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="b31fd-113">Sinus inverse (ASIN (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="b31fd-114">ATAN (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="b31fd-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="b31fd-115">Cosinus inverse (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="b31fd-116">ATAN (-x/sqrt (-x \* x + 1)) + 2 \* ATAN (1)</span><span class="sxs-lookup"><span data-stu-id="b31fd-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="b31fd-117">Inverse inverse (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="b31fd-118">2 \* ATAN (1) – ATAN (Sign (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="b31fd-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="b31fd-119">Cosécante inverse (ACSC (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="b31fd-120">ATAN (Sign (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="b31fd-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="b31fd-121">Cotangente inverse (acot (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="b31fd-122">2 \* ATAN (1)-ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="b31fd-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="b31fd-123">Sinus hyperbolique (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="b31fd-124">(Exp (x) – exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="b31fd-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="b31fd-125">Cosinus hyperbolique (Cosh (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="b31fd-126">(Exp (x) + exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="b31fd-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="b31fd-127">Tangente hyperbolique (TANH (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="b31fd-128">(Exp (x) – exp (-x))/(exp (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="b31fd-129">Sécante hyperbolique (sech (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="b31fd-130">2/(exp (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="b31fd-131">Cosécante hyperbolique (Csch (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="b31fd-132">2/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="b31fd-133">Cotangente hyperbolique (coth (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="b31fd-134">(Exp (x) + exp (-x))/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="b31fd-135">Sinus hyperbolique inverse (asinh (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="b31fd-136">Log (x + sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="b31fd-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="b31fd-137">Cosinus hyperbolique inverse (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="b31fd-138">Log (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="b31fd-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="b31fd-139">Tangente hyperbolique inverse (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="b31fd-140">Log ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="b31fd-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="b31fd-141">Sécante hyperbolique inverse (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="b31fd-142">Log ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="b31fd-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="b31fd-143">Cosécante hyperbolique inverse (acsch (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="b31fd-144">Log ((Sign (x) \* sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="b31fd-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="b31fd-145">Cotangente hyperbolique inverse (acoth (x))</span><span class="sxs-lookup"><span data-stu-id="b31fd-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="b31fd-146">Log ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="b31fd-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b31fd-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b31fd-147">See also</span></span>

- [<span data-ttu-id="b31fd-148">Fonctions mathématiques</span><span class="sxs-lookup"><span data-stu-id="b31fd-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
