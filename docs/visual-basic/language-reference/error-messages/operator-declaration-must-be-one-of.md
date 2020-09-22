---
title: 'La déclaration d’opérateur doit être l’une des suivantes : +,-, *,-,-, ^, &amp; , like, mod, and, or, Xor, not,  <<,  >>, =,  <>, <, <=, >, >=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: c388b1b0762dd7475ca365a8a62228d0b5d59414
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873613"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="6cbbf-102">La déclaration d’opérateur doit être l’une des suivantes : +,-, \*, \, /, ^, &amp; , like, mod, and, or, Xor, not, \<\<, >>...</span><span class="sxs-lookup"><span data-stu-id="6cbbf-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>

<span data-ttu-id="6cbbf-103">Vous pouvez déclarer uniquement un opérateur éligible pour la surcharge.</span><span class="sxs-lookup"><span data-stu-id="6cbbf-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="6cbbf-104">Le tableau suivant répertorie les opérateurs que vous pouvez déclarer.</span><span class="sxs-lookup"><span data-stu-id="6cbbf-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="6cbbf-105">Type</span><span class="sxs-lookup"><span data-stu-id="6cbbf-105">Type</span></span>|<span data-ttu-id="6cbbf-106">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="6cbbf-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="6cbbf-107">Unaire</span><span class="sxs-lookup"><span data-stu-id="6cbbf-107">Unary</span></span>|<span data-ttu-id="6cbbf-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="6cbbf-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="6cbbf-109">Binary</span><span class="sxs-lookup"><span data-stu-id="6cbbf-109">Binary</span></span>|<span data-ttu-id="6cbbf-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="6cbbf-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="6cbbf-111">Conversion (unaire)</span><span class="sxs-lookup"><span data-stu-id="6cbbf-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="6cbbf-112">Notez que l’opérateur `=` dans la liste binaire est l’opérateur de comparaison, et non l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="6cbbf-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="6cbbf-113">**ID d’erreur :** BC33000</span><span class="sxs-lookup"><span data-stu-id="6cbbf-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6cbbf-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6cbbf-114">To correct this error</span></span>  
  
1. <span data-ttu-id="6cbbf-115">Sélectionnez un opérateur dans le jeu d’opérateurs surchargeables.</span><span class="sxs-lookup"><span data-stu-id="6cbbf-115">Select an operator from the set of overloadable operators.</span></span>  
  
2. <span data-ttu-id="6cbbf-116">Si vous avez besoin des fonctionnalités de surcharge d’un opérateur que vous ne pouvez pas surcharger directement, créez une procédure `Function` qui accepte les paramètres appropriés et retourne la valeur adéquate.</span><span class="sxs-lookup"><span data-stu-id="6cbbf-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbbf-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cbbf-117">See also</span></span>

- [<span data-ttu-id="6cbbf-118">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="6cbbf-118">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="6cbbf-119">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="6cbbf-119">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="6cbbf-120">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="6cbbf-120">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="6cbbf-121">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="6cbbf-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="6cbbf-122">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="6cbbf-122">Function Statement</span></span>](../statements/function-statement.md)
