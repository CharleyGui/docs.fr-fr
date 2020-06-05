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
ms.openlocfilehash: 611f3d8faf2148b8a983467d9ace4fd6c18b30e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373881"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="19cb5-102">Fonctions mathématiques dérivées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19cb5-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="19cb5-103">Le tableau suivant répertorie les fonctions mathématiques non intrinsèques qui peuvent être dérivées des fonctions mathématiques intrinsèques de l' <xref:System.Math?displayProperty=nameWithType> objet.</span><span class="sxs-lookup"><span data-stu-id="19cb5-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="19cb5-104">Vous pouvez accéder aux fonctions mathématiques intrinsèques en ajoutant `Imports System.Math` à votre fichier ou projet.</span><span class="sxs-lookup"><span data-stu-id="19cb5-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="19cb5-105">Fonction</span><span class="sxs-lookup"><span data-stu-id="19cb5-105">Function</span></span>|<span data-ttu-id="19cb5-106">Équivalents dérivés</span><span class="sxs-lookup"><span data-stu-id="19cb5-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="19cb5-107">Sécante (sec (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-107">Secant (Sec(x))</span></span>|<span data-ttu-id="19cb5-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="19cb5-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="19cb5-109">Cosécante (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="19cb5-110">1/Sin (x)</span><span class="sxs-lookup"><span data-stu-id="19cb5-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="19cb5-111">Cotangente (CTAN (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="19cb5-112">1/Tan (x)</span><span class="sxs-lookup"><span data-stu-id="19cb5-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="19cb5-113">Sinus inverse (ASIN (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="19cb5-114">ATAN (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="19cb5-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="19cb5-115">Cosinus inverse (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="19cb5-116">ATAN (-x/sqrt (-x \* x + 1)) + 2 \* ATAN (1)</span><span class="sxs-lookup"><span data-stu-id="19cb5-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="19cb5-117">Inverse inverse (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="19cb5-118">2 \* ATAN (1) – ATAN (Sign (x)/sqrt (x \* x-1))</span><span class="sxs-lookup"><span data-stu-id="19cb5-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="19cb5-119">Cosécante inverse (ACSC (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="19cb5-120">ATAN (Sign (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="19cb5-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="19cb5-121">Cotangente inverse (acot (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="19cb5-122">2 \* ATAN (1)-ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="19cb5-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="19cb5-123">Sinus hyperbolique (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="19cb5-124">(Exp (x) – exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="19cb5-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="19cb5-125">Cosinus hyperbolique (Cosh (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="19cb5-126">(Exp (x) + exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="19cb5-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="19cb5-127">Tangente hyperbolique (TANH (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="19cb5-128">(Exp (x) – exp (-x))/(exp (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="19cb5-129">Sécante hyperbolique (sech (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="19cb5-130">2/(exp (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="19cb5-131">Cosécante hyperbolique (Csch (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="19cb5-132">2/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="19cb5-133">Cotangente hyperbolique (coth (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="19cb5-134">(Exp (x) + exp (-x))/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="19cb5-135">Sinus hyperbolique inverse (asinh (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="19cb5-136">Log (x + sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="19cb5-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="19cb5-137">Cosinus hyperbolique inverse (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="19cb5-138">Log (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="19cb5-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="19cb5-139">Tangente hyperbolique inverse (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="19cb5-140">Log ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="19cb5-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="19cb5-141">Sécante hyperbolique inverse (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="19cb5-142">Log ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="19cb5-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="19cb5-143">Cosécante hyperbolique inverse (acsch (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="19cb5-144">Log ((Sign (x) \* sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="19cb5-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="19cb5-145">Cotangente hyperbolique inverse (acoth (x))</span><span class="sxs-lookup"><span data-stu-id="19cb5-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="19cb5-146">Log ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="19cb5-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19cb5-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19cb5-147">See also</span></span>

- [<span data-ttu-id="19cb5-148">Fonctions mathématiques</span><span class="sxs-lookup"><span data-stu-id="19cb5-148">Math Functions</span></span>](../functions/math-functions.md)
