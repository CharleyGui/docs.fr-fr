---
title: Le constructeur '<name>' ne peut pas s'appeler lui-même
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: f40319cde8388b17e27cfaec2117ebd519ebd4ff
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160943"
---
# <a name="bc30298-constructor-name-cannot-call-itself"></a><span data-ttu-id="037fd-102">BC30298 : le constructeur' \<name> 'ne peut pas s’appeler lui-même</span><span class="sxs-lookup"><span data-stu-id="037fd-102">BC30298: Constructor '\<name>' cannot call itself</span></span>

<span data-ttu-id="037fd-103">Une `Sub New` procédure dans une classe ou une structure s’appelle elle-même.</span><span class="sxs-lookup"><span data-stu-id="037fd-103">A `Sub New` procedure in a class or structure calls itself.</span></span>

 <span data-ttu-id="037fd-104">L’objectif d’un constructeur est d’initialiser une instance d’une classe ou d’une structure lorsqu’elle est créée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="037fd-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="037fd-105">Une classe ou une structure peut avoir plusieurs constructeurs, à condition qu’ils aient tous des listes de paramètres différentes.</span><span class="sxs-lookup"><span data-stu-id="037fd-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="037fd-106">Un constructeur est autorisé à appeler un autre constructeur pour exécuter ses fonctionnalités en plus de lui-même.</span><span class="sxs-lookup"><span data-stu-id="037fd-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="037fd-107">Mais cela n’a pas de sens qu’un constructeur s’appelle lui-même et, en fait, cela entraînerait une récurrence infinie si elle était autorisée.</span><span class="sxs-lookup"><span data-stu-id="037fd-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>

 <span data-ttu-id="037fd-108">**ID d’erreur :** BC30298</span><span class="sxs-lookup"><span data-stu-id="037fd-108">**Error ID:** BC30298</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="037fd-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="037fd-109">To correct this error</span></span>

1. <span data-ttu-id="037fd-110">Vérifiez la liste des paramètres du constructeur appelé.</span><span class="sxs-lookup"><span data-stu-id="037fd-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="037fd-111">Elle doit être différente de celle du constructeur qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="037fd-111">It should be different from that of the constructor making the call.</span></span>

2. <span data-ttu-id="037fd-112">Si vous n’envisagez pas d’appeler un autre constructeur, supprimez `Sub New` entièrement l’appel.</span><span class="sxs-lookup"><span data-stu-id="037fd-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>

## <a name="see-also"></a><span data-ttu-id="037fd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="037fd-113">See also</span></span>

- [<span data-ttu-id="037fd-114">Durée de vie d’un objet : création et destruction des objets</span><span class="sxs-lookup"><span data-stu-id="037fd-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
