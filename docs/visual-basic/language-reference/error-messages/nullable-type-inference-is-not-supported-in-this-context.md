---
title: L'inférence de type nullable n'est pas prise en charge dans ce contexte
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409385"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="afa14-102">L'inférence de type nullable n'est pas prise en charge dans ce contexte</span><span class="sxs-lookup"><span data-stu-id="afa14-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="afa14-103">Les types valeur et les structures peuvent être déclarés Nullable.</span><span class="sxs-lookup"><span data-stu-id="afa14-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="afa14-104">Toutefois, vous ne pouvez pas utiliser la déclaration Nullable en association avec l’inférence de type.</span><span class="sxs-lookup"><span data-stu-id="afa14-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="afa14-105">Les exemples suivants provoquent cette erreur.</span><span class="sxs-lookup"><span data-stu-id="afa14-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="afa14-106">**ID d’erreur :** BC36629</span><span class="sxs-lookup"><span data-stu-id="afa14-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="afa14-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="afa14-107">To correct this error</span></span>  
  
- <span data-ttu-id="afa14-108">Utilisez une `As` clause pour déclarer la variable en tant que type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="afa14-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa14-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afa14-109">See also</span></span>

- [<span data-ttu-id="afa14-110">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="afa14-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="afa14-111">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="afa14-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
