---
title: Constantes et énumérations
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants [Visual Basic]
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants [Visual Basic], enumerations
- naming conventions [Visual Basic], constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
ms.openlocfilehash: 7d15c46c0f6bb00c23dd98e464f61a5f94b0773a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414400"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="7b99c-102">Constantes et énumérations en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b99c-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="7b99c-103">Les constantes sont un moyen d’utiliser des noms significatifs à la place d’une valeur qui ne change pas.</span><span class="sxs-lookup"><span data-stu-id="7b99c-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="7b99c-104">Les constantes stockent des valeurs qui, comme leur nom l’indique, demeurent constantes tout au long de l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="7b99c-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="7b99c-105">Vous pouvez utiliser des constantes pour spécifier des noms explicites au lieu de nombres, ce qui rend votre code plus lisible.</span><span class="sxs-lookup"><span data-stu-id="7b99c-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="7b99c-106">Les énumérations offrent un moyen pratique de travailler avec des ensembles de constantes connexes et d’associer des valeurs de constantes à des noms.</span><span class="sxs-lookup"><span data-stu-id="7b99c-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="7b99c-107">Par exemple, vous pouvez déclarer une énumération pour un ensemble de constantes entières associées aux jours de la semaine puis utiliser les noms des jours au lieu de leur valeur entière dans votre code.</span><span class="sxs-lookup"><span data-stu-id="7b99c-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b99c-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7b99c-108">In This Section</span></span>  
  
|<span data-ttu-id="7b99c-109">Terme</span><span class="sxs-lookup"><span data-stu-id="7b99c-109">Term</span></span>|<span data-ttu-id="7b99c-110">Définition</span><span class="sxs-lookup"><span data-stu-id="7b99c-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="7b99c-111">Vue d'ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="7b99c-111">Constants Overview</span></span>](constants-overview.md)|<span data-ttu-id="7b99c-112">Les rubriques de cette section décrivent les constantes et leurs utilisations.</span><span class="sxs-lookup"><span data-stu-id="7b99c-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="7b99c-113">Vue d'ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="7b99c-113">Enumerations Overview</span></span>](enumerations-overview.md)|<span data-ttu-id="7b99c-114">Les rubriques de cette section décrivent les énumérations et leurs utilisations.</span><span class="sxs-lookup"><span data-stu-id="7b99c-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="7b99c-115">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="7b99c-115">Related Sections</span></span>  
  
|<span data-ttu-id="7b99c-116">Terme</span><span class="sxs-lookup"><span data-stu-id="7b99c-116">Term</span></span>|<span data-ttu-id="7b99c-117">Définition</span><span class="sxs-lookup"><span data-stu-id="7b99c-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="7b99c-118">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="7b99c-118">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="7b99c-119">Décrit l’instruction `Const`, qui est utilisée pour déclarer des constantes.</span><span class="sxs-lookup"><span data-stu-id="7b99c-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="7b99c-120">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="7b99c-120">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)|<span data-ttu-id="7b99c-121">Décrit l’instruction `Enum`, qui est utilisée pour créer des énumérations.</span><span class="sxs-lookup"><span data-stu-id="7b99c-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="7b99c-122">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="7b99c-122">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="7b99c-123">Décrit l’instruction `Option Explicit`, qui est utilisée au niveau d’un module pour forcer la déclaration explicite de toutes les variables de ce module.</span><span class="sxs-lookup"><span data-stu-id="7b99c-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="7b99c-124">Instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="7b99c-124">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)|<span data-ttu-id="7b99c-125">Décrit l’instruction `Option Infer`, qui permet l’utilisation de l’inférence de type locale dans la déclaration des variables.</span><span class="sxs-lookup"><span data-stu-id="7b99c-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="7b99c-126">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="7b99c-126">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="7b99c-127">Décrit l’instruction `Option Strict`, qui limite les conversions des types de données implicites aux seules conversions étendues, interdit les liaisons tardives et interdit pas le typage implicite qui aboutit à un type `Object`.</span><span class="sxs-lookup"><span data-stu-id="7b99c-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
