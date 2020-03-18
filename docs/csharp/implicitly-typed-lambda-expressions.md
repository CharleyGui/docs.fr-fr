---
title: Expressions lambda implicitement typées
description: Découvrez pourquoi vous ne pouvez pas utiliser une déclaration de variable implicitement typée pour déclarer une expression lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145720"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="26c55-103">Expressions lambda implicitement typées</span><span class="sxs-lookup"><span data-stu-id="26c55-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="26c55-104">Vous ne pouvez pas utiliser une déclaration de variable implicitement typée pour déclarer une expression lambda,</span><span class="sxs-lookup"><span data-stu-id="26c55-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="26c55-105">car cela crée un problème de logique circulaire pour le compilateur.</span><span class="sxs-lookup"><span data-stu-id="26c55-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="26c55-106">La déclaration `var` indique au compilateur de déterminer le type de la variable à partir du type de l’expression située à droite de l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="26c55-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="26c55-107">Une expression lambda n’a pas de type au moment de la compilation, mais elle peut être convertie en n’importe quel type d’expression ou de délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="26c55-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="26c55-108">Quand vous assignez une expression lambda à une variable d’un type de délégué ou d’expression, vous indiquez au compilateur de convertir l’expression lambda en une expression ou un délégué qui corresponde à la signature de la variable assignée.</span><span class="sxs-lookup"><span data-stu-id="26c55-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="26c55-109">Le compilateur doit tenter de faire correspondre ce qui se trouve à droite de l’assignation avec ce qui se trouve à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="26c55-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span>

<span data-ttu-id="26c55-110">Les deux côtés de l’assignation ne peuvent pas indiquer au compilateur d’examiner l’objet situé de l’autre côté de l’opérateur d’assignation et de vérifier si le type correspond.</span><span class="sxs-lookup"><span data-stu-id="26c55-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="26c55-111">Vous pouvez obtenir encore plus de détails sur les raisons pour lesquelles la langue C spécifie ce comportement en lisant [cet article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (téléchargement PDF).</span><span class="sxs-lookup"><span data-stu-id="26c55-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF download).</span></span>
