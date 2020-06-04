---
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 69040bf48b44a54f7a231738b88db1cbc716ebb3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359901"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="00e39-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00e39-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="00e39-103">Indique qu’un opérateur de conversion ( `CType` ) convertit une classe ou une structure en un type qui peut contenir toutes les valeurs possibles de la classe ou de la structure d’origine.</span><span class="sxs-lookup"><span data-stu-id="00e39-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="00e39-104">Conversion avec le mot clé Widening</span><span class="sxs-lookup"><span data-stu-id="00e39-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="00e39-105">La procédure de conversion doit spécifier `Public Shared` en plus de `Widening` .</span><span class="sxs-lookup"><span data-stu-id="00e39-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="00e39-106">Les conversions étendues fonctionnent toujours au moment de l’exécution et n’entraînent jamais de perte de données.</span><span class="sxs-lookup"><span data-stu-id="00e39-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="00e39-107">Les exemples sont `Single` pour `Double` , `Char` à `String` et un type dérivé dans son type de base.</span><span class="sxs-lookup"><span data-stu-id="00e39-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="00e39-108">Cette dernière conversion est étendue car le type dérivé contient tous les membres du type de base et est donc une instance du type de base.</span><span class="sxs-lookup"><span data-stu-id="00e39-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="00e39-109">Le code de consommation n’a pas besoin d’utiliser `CType` pour les conversions étendues, même si `Option Strict` est `On` .</span><span class="sxs-lookup"><span data-stu-id="00e39-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="00e39-110">Le `Widening` mot clé peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="00e39-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="00e39-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="00e39-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="00e39-112">Pour obtenir des exemples de définitions d’opérateurs de conversion étendues et restrictives, consultez [Comment : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="00e39-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e39-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00e39-113">See also</span></span>

- [<span data-ttu-id="00e39-114">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="00e39-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="00e39-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="00e39-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="00e39-116">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="00e39-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="00e39-117">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="00e39-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="00e39-118">CType Function</span><span class="sxs-lookup"><span data-stu-id="00e39-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="00e39-119">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="00e39-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="00e39-120">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="00e39-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
