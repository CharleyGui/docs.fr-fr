---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: f7724053e3732c909523e4e2d3b65bb1918c29d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362357"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="5b077-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b077-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="5b077-103">Indique qu’un opérateur de conversion ( `CType` ) convertit une classe ou une structure en un type qui peut ne pas pouvoir contenir certaines des valeurs possibles de la classe ou de la structure d’origine.</span><span class="sxs-lookup"><span data-stu-id="5b077-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="5b077-104">Conversion avec le mot clé restrictive</span><span class="sxs-lookup"><span data-stu-id="5b077-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="5b077-105">La procédure de conversion doit spécifier `Public Shared` en plus de `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="5b077-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="5b077-106">Les conversions restrictives ne réussissent pas toujours au moment de l’exécution et peuvent échouer ou entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="5b077-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="5b077-107">Exemples : `Long` à `Integer` , `String` à `Date` et un type de base à un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="5b077-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="5b077-108">Cette dernière conversion est restrictive, car le type de base ne peut pas contenir tous les membres du type dérivé et, par conséquent, n’est pas une instance du type dérivé.</span><span class="sxs-lookup"><span data-stu-id="5b077-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="5b077-109">Si `Option Strict` est `On` , le code de consommation doit utiliser `CType` pour toutes les conversions restrictives.</span><span class="sxs-lookup"><span data-stu-id="5b077-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="5b077-110">Le `Narrowing` mot clé peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="5b077-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="5b077-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="5b077-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b077-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b077-112">See also</span></span>

- [<span data-ttu-id="5b077-113">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="5b077-113">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="5b077-114">Widening</span><span class="sxs-lookup"><span data-stu-id="5b077-114">Widening</span></span>](widening.md)
- [<span data-ttu-id="5b077-115">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="5b077-115">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="5b077-116">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="5b077-116">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="5b077-117">CType Function</span><span class="sxs-lookup"><span data-stu-id="5b077-117">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="5b077-118">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="5b077-118">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
