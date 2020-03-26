---
title: L'inférence de type nullable n'est pas prise en charge dans ce contexte
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249498"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="6ecab-102">L'inférence de type nullable n'est pas prise en charge dans ce contexte</span><span class="sxs-lookup"><span data-stu-id="6ecab-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="6ecab-103">Les types et les structures de valeur peuvent être déclarés nuls.</span><span class="sxs-lookup"><span data-stu-id="6ecab-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="6ecab-104">Toutefois, vous ne pouvez pas utiliser la déclaration annulée en combinaison avec l’inférence de type.</span><span class="sxs-lookup"><span data-stu-id="6ecab-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="6ecab-105">Les exemples suivants causent cette erreur.</span><span class="sxs-lookup"><span data-stu-id="6ecab-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="6ecab-106">**ID erreur:** BC36629</span><span class="sxs-lookup"><span data-stu-id="6ecab-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ecab-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6ecab-107">To correct this error</span></span>  
  
- <span data-ttu-id="6ecab-108">Utilisez `As` une clause pour déclarer la variable comme un type de valeur nulle.</span><span class="sxs-lookup"><span data-stu-id="6ecab-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ecab-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ecab-109">See also</span></span>

- [<span data-ttu-id="6ecab-110">Types de valeur nuls</span><span class="sxs-lookup"><span data-stu-id="6ecab-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="6ecab-111">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="6ecab-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
