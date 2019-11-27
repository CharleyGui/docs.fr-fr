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
# <a name="derived-math-functions-visual-basic"></a>Fonctions mathématiques dérivées (Visual Basic)
Le tableau suivant répertorie les fonctions mathématiques non intrinsèques qui peuvent être dérivées des fonctions mathématiques intrinsèques de l’objet <xref:System.Math?displayProperty=nameWithType>. Vous pouvez accéder aux fonctions mathématiques intrinsèques en ajoutant des `Imports System.Math` à votre fichier ou projet.  
  
|Fonction|Équivalents dérivés|  
|--------------|-------------------------|  
|Sécante (sec (x))|1/cos (x)|  
|Cosécante (CSC (x))|1/Sin (x)|  
|Cotangente (CTAN (x))|1/Tan (x)|  
|Sinus inverse (ASIN (x))|ATAN (x/sqrt (-x * x + 1))|  
|Cosinus inverse (ACOS (x))|ATAN (-x/sqrt (-x * x + 1)) + 2 \* ATAN (1)|  
|Inverse inverse (ASEC (x))|2 * ATAN (1) – ATAN (Sign (x)/sqrt (x \* x – 1))|  
|Cosécante inverse (ACSC (x))|ATAN (Sign (x)/sqrt (x * x – 1))|  
|Cotangente inverse (acot (x))|2 * ATAN (1)-ATAN (x)|  
|Sinus hyperbolique (sinh (x))|(Exp (x) – exp (-x))/2|  
|Cosinus hyperbolique (Cosh (x))|(Exp (x) + exp (-x))/2|  
|Tangente hyperbolique (TANH (x))|(Exp (x) – exp (-x))/(exp (x) + exp (-x))|  
|Sécante hyperbolique (sech (x))|2/(exp (x) + exp (-x))|  
|Cosécante hyperbolique (Csch (x))|2/(exp (x) – exp (-x))|  
|Cotangente hyperbolique (coth (x))|(Exp (x) + exp (-x))/(exp (x) – exp (-x))|  
|Sinus hyperbolique inverse (asinh (x))|Log (x + sqrt (x * x + 1))|  
|Cosinus hyperbolique inverse (ACOSH (x))|Log (x + sqrt (x * x – 1))|  
|Tangente hyperbolique inverse (ATANH (x))|Log ((1 + x)/(1 – x))/2|  
|Sécante hyperbolique inverse (AsecH (x))|Log ((sqrt (-x * x + 1) + 1)/x)|  
|Cosécante hyperbolique inverse (acsch (x))|Log ((Sign (x) * sqrt (x \* x + 1) + 1)/x)|  
|Cotangente hyperbolique inverse (acoth (x))|Log ((x + 1)/(x – 1))/2|  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions mathématiques](../../../visual-basic/language-reference/functions/math-functions.md)
