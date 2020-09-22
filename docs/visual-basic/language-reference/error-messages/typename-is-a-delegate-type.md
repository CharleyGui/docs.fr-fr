---
title: "'<typename>' est un type délégué"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4cc0a1221dcf65aa2a16fd7d82568c8544f27fdb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875083"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="7c4f9-102">'\<typename>' est un type délégué</span><span class="sxs-lookup"><span data-stu-id="7c4f9-102">'\<typename>' is a delegate type</span></span>

<span data-ttu-id="7c4f9-103">' \<typename> 'est un type délégué.</span><span class="sxs-lookup"><span data-stu-id="7c4f9-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="7c4f9-104">La construction de délégué autorise uniquement une seule expression AddressOf comme liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="7c4f9-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="7c4f9-105">Souvent, une expression AddressOf peut être utilisée à la place d’une construction de délégué.</span><span class="sxs-lookup"><span data-stu-id="7c4f9-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="7c4f9-106">Une `New` clause qui crée une instance d’une classe déléguée fournit une liste d’arguments non valide au constructeur délégué.</span><span class="sxs-lookup"><span data-stu-id="7c4f9-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="7c4f9-107">Vous ne pouvez fournir qu’une seule `AddressOf` expression lors de la création d’une instance de délégué.</span><span class="sxs-lookup"><span data-stu-id="7c4f9-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="7c4f9-108">Cette erreur peut se produire si vous ne transmettez pas d’arguments au constructeur délégué, si vous transmettez plusieurs arguments ou si vous transmettez un argument unique qui n’est pas une `AddressOf` expression valide.</span><span class="sxs-lookup"><span data-stu-id="7c4f9-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="7c4f9-109">**ID d’erreur :** BC32008</span><span class="sxs-lookup"><span data-stu-id="7c4f9-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7c4f9-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="7c4f9-110">To correct this error</span></span>  
  
- <span data-ttu-id="7c4f9-111">Utilisez une `AddressOf` expression unique dans la liste d’arguments pour la classe déléguée dans la `New` clause.</span><span class="sxs-lookup"><span data-stu-id="7c4f9-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4f9-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c4f9-112">See also</span></span>

- [<span data-ttu-id="7c4f9-113">Nouvel opérateur</span><span class="sxs-lookup"><span data-stu-id="7c4f9-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="7c4f9-114">AddressOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="7c4f9-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="7c4f9-115">Délégués</span><span class="sxs-lookup"><span data-stu-id="7c4f9-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="7c4f9-116">Comment : appeler une méthode déléguée</span><span class="sxs-lookup"><span data-stu-id="7c4f9-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
