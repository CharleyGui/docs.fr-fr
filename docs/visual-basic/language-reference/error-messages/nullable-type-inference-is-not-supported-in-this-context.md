---
title: L'inférence de type nullable n'est pas prise en charge dans ce contexte
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 610d2dc427d882c412b87eb67f021a8a86025f25
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159924"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="1fd46-102">BC36629 : l’inférence de type Nullable n’est pas prise en charge dans ce contexte</span><span class="sxs-lookup"><span data-stu-id="1fd46-102">BC36629: Nullable type inference is not supported in this context</span></span>

<span data-ttu-id="1fd46-103">Les types valeur et les structures peuvent être déclarés Nullable.</span><span class="sxs-lookup"><span data-stu-id="1fd46-103">Value types and structures can be declared nullable.</span></span>

```vb
Dim a? As Integer
Dim b As Integer?
```

 <span data-ttu-id="1fd46-104">Toutefois, vous ne pouvez pas utiliser la déclaration Nullable en association avec l’inférence de type.</span><span class="sxs-lookup"><span data-stu-id="1fd46-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="1fd46-105">Les exemples suivants provoquent cette erreur.</span><span class="sxs-lookup"><span data-stu-id="1fd46-105">The following examples cause this error.</span></span>

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 <span data-ttu-id="1fd46-106">**ID d’erreur :** BC36629</span><span class="sxs-lookup"><span data-stu-id="1fd46-106">**Error ID:** BC36629</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1fd46-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="1fd46-107">To correct this error</span></span>

- <span data-ttu-id="1fd46-108">Utilisez une `As` clause pour déclarer la variable en tant que type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="1fd46-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fd46-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fd46-109">See also</span></span>

- [<span data-ttu-id="1fd46-110">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="1fd46-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="1fd46-111">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="1fd46-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
