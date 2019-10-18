---
title: Impossible de déduire le ou les types de données du ou des paramètres de type à partir de ces arguments
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 97b03874489473482554078958c7bfd29d87c095
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523997"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="10172-102">Impossible de déduire le ou les types de données du ou des paramètres de type à partir de ces arguments</span><span class="sxs-lookup"><span data-stu-id="10172-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>

<span data-ttu-id="10172-103">Impossible de déduire le ou les types de données du ou des paramètres de type à partir de ces arguments.</span><span class="sxs-lookup"><span data-stu-id="10172-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="10172-104">La spécification explicite du ou des types de données peut permettre de corriger cette erreur.</span><span class="sxs-lookup"><span data-stu-id="10172-104">Specifying the data type(s) explicitly might correct this error.</span></span>

<span data-ttu-id="10172-105">Cette erreur se produit quand la résolution de surcharge a échoué.</span><span class="sxs-lookup"><span data-stu-id="10172-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="10172-106">Elle entraîne l’affichage d’un message subordonné qui indique pourquoi un candidat de surcharge particulier a été éliminé.</span><span class="sxs-lookup"><span data-stu-id="10172-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="10172-107">Le message d’erreur explique que le compilateur ne peut pas utiliser l’inférence de type pour rechercher des types de données pour les paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="10172-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="10172-108">Quand la spécification des arguments n’est pas une option (par exemple, pour les opérateurs de requête dans les expressions de requête), le message d’erreur apparaît sans la deuxième phrase.</span><span class="sxs-lookup"><span data-stu-id="10172-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>

<span data-ttu-id="10172-109">Le code suivant illustre cette erreur.</span><span class="sxs-lookup"><span data-stu-id="10172-109">The following code demonstrates the error.</span></span>

```vb
Module Module1

    Sub Main()

        '' Not Valid.
        'OverloadedGenericMethod("Hello", "World")

    End Sub

    Sub OverloadedGenericMethod(Of T)(ByVal x As String,
                                      ByVal y As InterfaceExample(Of T))
    End Sub

    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,
                                         ByVal y As InterfaceExample(Of R))
    End Sub

End Module

Interface InterfaceExample(Of T)
End Interface
```

<span data-ttu-id="10172-110">**ID d’erreur :** BC36647 et BC36644</span><span class="sxs-lookup"><span data-stu-id="10172-110">**Error ID:** BC36647 and BC36644</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="10172-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="10172-111">To correct this error</span></span>

<span data-ttu-id="10172-112">Vous pourrez peut-être spécifier un type de données pour le ou les paramètres de type au lieu de compter sur l’inférence de type.</span><span class="sxs-lookup"><span data-stu-id="10172-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>

## <a name="see-also"></a><span data-ttu-id="10172-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10172-113">See also</span></span>

- [<span data-ttu-id="10172-114">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="10172-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="10172-115">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10172-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="10172-116">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10172-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
