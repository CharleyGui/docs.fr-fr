---
title: "'<typename>' est un type délégué"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: dcb52188c53b38ac14de0002b5212bb33c9f7203
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161775"
---
# <a name="bc32008-typename-is-a-delegate-type"></a><span data-ttu-id="59af4-102">BC32008 : ' \<typename> 'est un type délégué</span><span class="sxs-lookup"><span data-stu-id="59af4-102">BC32008: '\<typename>' is a delegate type</span></span>

<span data-ttu-id="59af4-103">' \<typename> 'est un type délégué.</span><span class="sxs-lookup"><span data-stu-id="59af4-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="59af4-104">La construction de délégué autorise uniquement une seule expression AddressOf comme liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="59af4-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="59af4-105">Souvent, une expression AddressOf peut être utilisée à la place d’une construction de délégué.</span><span class="sxs-lookup"><span data-stu-id="59af4-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>

 <span data-ttu-id="59af4-106">Une `New` clause qui crée une instance d’une classe déléguée fournit une liste d’arguments non valide au constructeur délégué.</span><span class="sxs-lookup"><span data-stu-id="59af4-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>

 <span data-ttu-id="59af4-107">Vous ne pouvez fournir qu’une seule `AddressOf` expression lors de la création d’une instance de délégué.</span><span class="sxs-lookup"><span data-stu-id="59af4-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>

 <span data-ttu-id="59af4-108">Cette erreur peut se produire si vous ne transmettez pas d’arguments au constructeur délégué, si vous transmettez plusieurs arguments ou si vous transmettez un argument unique qui n’est pas une `AddressOf` expression valide.</span><span class="sxs-lookup"><span data-stu-id="59af4-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>

 <span data-ttu-id="59af4-109">**ID d’erreur :** BC32008</span><span class="sxs-lookup"><span data-stu-id="59af4-109">**Error ID:** BC32008</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="59af4-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="59af4-110">To correct this error</span></span>

- <span data-ttu-id="59af4-111">Utilisez une `AddressOf` expression unique dans la liste d’arguments pour la classe déléguée dans la `New` clause.</span><span class="sxs-lookup"><span data-stu-id="59af4-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="59af4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59af4-112">See also</span></span>

- [<span data-ttu-id="59af4-113">Nouvel opérateur</span><span class="sxs-lookup"><span data-stu-id="59af4-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="59af4-114">AddressOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="59af4-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="59af4-115">Délégués</span><span class="sxs-lookup"><span data-stu-id="59af4-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="59af4-116">Comment : appeler une méthode déléguée</span><span class="sxs-lookup"><span data-stu-id="59af4-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
