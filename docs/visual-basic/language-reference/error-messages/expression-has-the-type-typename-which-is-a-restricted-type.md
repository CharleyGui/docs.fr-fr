---
title: L'expression a le type '<typename>', qui est un type restreint et qui ne peut pas être utilisé pour accéder aux membres hérités de 'Object' ou 'ValueType'
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 7fc3f36b28677ed5ebcc0b579f009c796dd431ff
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874221"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="4e34d-102">L'expression a le type '\<typename>', qui est un type restreint et qui ne peut pas être utilisé pour accéder aux membres hérités de 'Object' ou 'ValueType'</span><span class="sxs-lookup"><span data-stu-id="4e34d-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>

<span data-ttu-id="4e34d-103">Une expression prend la valeur d’un type qui ne peut pas être boxed par le common language runtime (CLR), mais accède à un membre qui requiert la conversion boxing.</span><span class="sxs-lookup"><span data-stu-id="4e34d-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="4e34d-104">Le*boxing* est le traitement nécessaire à la conversion d’un type en `Object` ou, à l’occasion, en <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="4e34d-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="4e34d-105">La common language runtime ne peut pas Box certains types de structures, par exemple, <xref:System.ArgIterator> <xref:System.RuntimeArgumentHandle> et <xref:System.TypedReference> .</span><span class="sxs-lookup"><span data-stu-id="4e34d-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="4e34d-106">Cette expression tente d’utiliser le type restreint pour appeler une méthode héritée de <xref:System.Object> ou <xref:System.ValueType> , telle que <xref:System.Object.GetHashCode%2A> ou <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="4e34d-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="4e34d-107">Pour accéder à cette méthode, Visual Basic a tenté une conversion boxing implicite qui provoque cette erreur.</span><span class="sxs-lookup"><span data-stu-id="4e34d-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="4e34d-108">**ID d’erreur :** BC31393</span><span class="sxs-lookup"><span data-stu-id="4e34d-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4e34d-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="4e34d-109">To correct this error</span></span>  
  
1. <span data-ttu-id="4e34d-110">Recherchez l’expression évaluée comme étant le type cité.</span><span class="sxs-lookup"><span data-stu-id="4e34d-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2. <span data-ttu-id="4e34d-111">Recherchez la partie de votre instruction qui tente d’appeler la méthode héritée de <xref:System.Object> ou <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="4e34d-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3. <span data-ttu-id="4e34d-112">Réécrivez l’instruction pour éviter l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4e34d-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e34d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e34d-113">See also</span></span>

- [<span data-ttu-id="4e34d-114">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="4e34d-114">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
