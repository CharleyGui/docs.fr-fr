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
ms.openlocfilehash: 77515357ac9dc972992df09c471695aad13985c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867929"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="0c7a9-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c7a9-102">Narrowing (Visual Basic)</span></span>

<span data-ttu-id="0c7a9-103">Indique qu’un opérateur de conversion ( `CType` ) convertit une classe ou une structure en un type qui peut ne pas pouvoir contenir certaines des valeurs possibles de la classe ou de la structure d’origine.</span><span class="sxs-lookup"><span data-stu-id="0c7a9-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="0c7a9-104">Conversion avec le mot clé restrictive</span><span class="sxs-lookup"><span data-stu-id="0c7a9-104">Converting with the Narrowing Keyword</span></span>  

 <span data-ttu-id="0c7a9-105">La procédure de conversion doit spécifier `Public Shared` en plus de `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="0c7a9-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="0c7a9-106">Les conversions restrictives ne réussissent pas toujours au moment de l’exécution et peuvent échouer ou entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="0c7a9-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="0c7a9-107">Exemples : `Long` à `Integer` , `String` à `Date` et un type de base à un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="0c7a9-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="0c7a9-108">Cette dernière conversion est restrictive, car le type de base ne peut pas contenir tous les membres du type dérivé et, par conséquent, n’est pas une instance du type dérivé.</span><span class="sxs-lookup"><span data-stu-id="0c7a9-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="0c7a9-109">Si `Option Strict` est `On` , le code de consommation doit utiliser `CType` pour toutes les conversions restrictives.</span><span class="sxs-lookup"><span data-stu-id="0c7a9-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="0c7a9-110">Le `Narrowing` mot clé peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="0c7a9-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="0c7a9-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="0c7a9-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c7a9-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c7a9-112">See also</span></span>

- [<span data-ttu-id="0c7a9-113">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="0c7a9-113">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="0c7a9-114">Widening</span><span class="sxs-lookup"><span data-stu-id="0c7a9-114">Widening</span></span>](widening.md)
- [<span data-ttu-id="0c7a9-115">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="0c7a9-115">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="0c7a9-116">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="0c7a9-116">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="0c7a9-117">CType Function</span><span class="sxs-lookup"><span data-stu-id="0c7a9-117">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="0c7a9-118">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="0c7a9-118">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
