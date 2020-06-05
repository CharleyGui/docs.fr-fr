---
title: Les arguments de type ne peuvent pas être déduits à partir du délégué
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f29e92c8245e33c0418d9a387070b03f645c331e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362746"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="25b89-102">Les arguments de type ne peuvent pas être déduits à partir du délégué</span><span class="sxs-lookup"><span data-stu-id="25b89-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="25b89-103">Une instruction d’assignation utilise `AddressOf` pour assigner l’adresse d’une procédure générique à un délégué, mais elle ne fournit aucun argument de type à la procédure générique.</span><span class="sxs-lookup"><span data-stu-id="25b89-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="25b89-104">En général, lorsque vous appelez un type générique, vous fournissez un argument de type pour chaque paramètre de type défini par le type générique.</span><span class="sxs-lookup"><span data-stu-id="25b89-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="25b89-105">Si vous ne fournissez pas d’arguments de type, le compilateur tente de déduire les types à passer aux paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="25b89-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="25b89-106">Si le contexte ne fournit pas au compilateur des informations suffisantes pour déduire les types, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="25b89-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="25b89-107">**ID d’erreur :** BC36564</span><span class="sxs-lookup"><span data-stu-id="25b89-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25b89-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="25b89-108">To correct this error</span></span>  
  
- <span data-ttu-id="25b89-109">Spécifiez les arguments de type pour la procédure générique dans l’expression `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="25b89-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b89-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25b89-110">See also</span></span>

- [<span data-ttu-id="25b89-111">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25b89-111">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="25b89-112">AddressOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="25b89-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="25b89-113">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25b89-113">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="25b89-114">Type List</span><span class="sxs-lookup"><span data-stu-id="25b89-114">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="25b89-115">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="25b89-115">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
