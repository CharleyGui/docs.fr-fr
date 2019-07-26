---
title: Le type de '<variablename>' ne peut pas être déduit, car les limites de la boucle et la clause d'incrémentation ne sont pas converties en un même type
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512707"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="ca580-102">Impossible de déduire le type de'\<NomVariable > ', car les limites de la boucle et la variable d’étape ne s’étendent pas au même type</span><span class="sxs-lookup"><span data-stu-id="ca580-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="ca580-103">Vous avez écrit une `For...Next` boucle dans laquelle le compilateur ne peut pas déduire un type de données pour la variable de contrôle de boucle, car les conditions suivantes sont vraies:</span><span class="sxs-lookup"><span data-stu-id="ca580-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="ca580-104">Le type de données de la variable de contrôle de boucle n’est pas spécifié avec une clause `As` .</span><span class="sxs-lookup"><span data-stu-id="ca580-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="ca580-105">Les limites de la boucle et l’incrémentation contiennent au moins deux types de données.</span><span class="sxs-lookup"><span data-stu-id="ca580-105">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="ca580-106">Il n’existe aucune conversion standard entre les types de données.</span><span class="sxs-lookup"><span data-stu-id="ca580-106">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="ca580-107">Par conséquent, le compilateur ne peut pas déduire le type de données d’une variable de contrôle de boucle.</span><span class="sxs-lookup"><span data-stu-id="ca580-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="ca580-108">Dans l’exemple suivant, la variable Step est un caractère et les limites de la boucle sont à la fois des entiers.</span><span class="sxs-lookup"><span data-stu-id="ca580-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="ca580-109">Étant donné qu’il n’existe pas de conversion standard entre les caractères et les entiers, cette erreur est signalée.</span><span class="sxs-lookup"><span data-stu-id="ca580-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="ca580-110">**ID d’erreur:** BC30982</span><span class="sxs-lookup"><span data-stu-id="ca580-110">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ca580-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ca580-111">To correct this error</span></span>

- <span data-ttu-id="ca580-112">Modifiez les types des limites de la boucle et de la variable d’étape si nécessaire afin qu’au moins l’un d’eux soit un type auquel les autres s’étendent.</span><span class="sxs-lookup"><span data-stu-id="ca580-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="ca580-113">Dans l’exemple précédent, remplacez le type de `stepVar` par `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ca580-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="ca580-114">ou</span><span class="sxs-lookup"><span data-stu-id="ca580-114">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="ca580-115">Utilisez des fonctions de conversion explicites pour convertir les limites de la boucle et la variable d’étape en types appropriés.</span><span class="sxs-lookup"><span data-stu-id="ca580-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="ca580-116">Dans l’exemple précédent, appliquez la `Val` fonction à `stepVar`.</span><span class="sxs-lookup"><span data-stu-id="ca580-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="ca580-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca580-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="ca580-118">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="ca580-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="ca580-119">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="ca580-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="ca580-120">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="ca580-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="ca580-121">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="ca580-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="ca580-122">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="ca580-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="ca580-123">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="ca580-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
