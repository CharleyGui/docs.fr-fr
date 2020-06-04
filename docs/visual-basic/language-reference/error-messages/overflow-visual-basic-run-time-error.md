---
title: Dépassement de capacité (erreur d'exécution Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387268"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="b08d4-102">Dépassement de capacité (erreur d'exécution Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b08d4-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="b08d4-103">Un dépassement de capacité se produit lorsque vous tentez une assignation qui dépasse les limites de la cible de l’assignation.</span><span class="sxs-lookup"><span data-stu-id="b08d4-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b08d4-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b08d4-104">To correct this error</span></span>  
  
1. <span data-ttu-id="b08d4-105">Assurez-vous que les résultats des assignations, des calculs et des conversions de types de données ne sont pas trop grands pour être représentés dans la plage de variables autorisées pour ce type de valeur, et attribuez la valeur à une variable d’un type qui peut contenir une plus grande plage de valeurs, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b08d4-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="b08d4-106">Assurez-vous que les assignations aux propriétés correspondent à la plage de la propriété dans laquelle elles sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="b08d4-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="b08d4-107">Assurez-vous que les nombres utilisés dans les calculs qui sont convertis en entiers n’ont pas de résultats plus grands que des entiers.</span><span class="sxs-lookup"><span data-stu-id="b08d4-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b08d4-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b08d4-108">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="b08d4-109">Types de données</span><span class="sxs-lookup"><span data-stu-id="b08d4-109">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="b08d4-110">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="b08d4-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
