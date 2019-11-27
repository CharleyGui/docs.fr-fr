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
ms.openlocfilehash: 858f22df26d44f47848921ee862c1d4c1ca1fc60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353983"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="1540e-102">Constantes et énumérations en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1540e-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="1540e-103">Les constantes sont un moyen d’utiliser des noms significatifs à la place d’une valeur qui ne change pas.</span><span class="sxs-lookup"><span data-stu-id="1540e-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="1540e-104">Les constantes stockent des valeurs qui, comme leur nom l’indique, demeurent constantes tout au long de l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="1540e-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="1540e-105">Vous pouvez utiliser des constantes pour spécifier des noms explicites au lieu de nombres, ce qui rend votre code plus lisible.</span><span class="sxs-lookup"><span data-stu-id="1540e-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="1540e-106">Les énumérations offrent un moyen pratique de travailler avec des ensembles de constantes connexes et d’associer des valeurs de constantes à des noms.</span><span class="sxs-lookup"><span data-stu-id="1540e-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="1540e-107">Par exemple, vous pouvez déclarer une énumération pour un ensemble de constantes entières associées aux jours de la semaine puis utiliser les noms des jours au lieu de leur valeur entière dans votre code.</span><span class="sxs-lookup"><span data-stu-id="1540e-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1540e-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1540e-108">In This Section</span></span>  
  
|<span data-ttu-id="1540e-109">Terme</span><span class="sxs-lookup"><span data-stu-id="1540e-109">Term</span></span>|<span data-ttu-id="1540e-110">Définition</span><span class="sxs-lookup"><span data-stu-id="1540e-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="1540e-111">Vue d’ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="1540e-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="1540e-112">Les rubriques de cette section décrivent les constantes et leurs utilisations.</span><span class="sxs-lookup"><span data-stu-id="1540e-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="1540e-113">Vue d’ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="1540e-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="1540e-114">Les rubriques de cette section décrivent les énumérations et leurs utilisations.</span><span class="sxs-lookup"><span data-stu-id="1540e-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="1540e-115">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="1540e-115">Related Sections</span></span>  
  
|<span data-ttu-id="1540e-116">Terme</span><span class="sxs-lookup"><span data-stu-id="1540e-116">Term</span></span>|<span data-ttu-id="1540e-117">Définition</span><span class="sxs-lookup"><span data-stu-id="1540e-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="1540e-118">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="1540e-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="1540e-119">Décrit l’instruction `Const`, qui est utilisée pour déclarer des constantes.</span><span class="sxs-lookup"><span data-stu-id="1540e-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="1540e-120">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="1540e-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="1540e-121">Décrit l’instruction `Enum`, qui est utilisée pour créer des énumérations.</span><span class="sxs-lookup"><span data-stu-id="1540e-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="1540e-122">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="1540e-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="1540e-123">Décrit l’instruction `Option Explicit`, qui est utilisée au niveau d’un module pour forcer la déclaration explicite de toutes les variables de ce module.</span><span class="sxs-lookup"><span data-stu-id="1540e-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="1540e-124">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="1540e-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="1540e-125">Décrit l’instruction `Option Infer`, qui permet l’utilisation de l’inférence de type locale dans la déclaration des variables.</span><span class="sxs-lookup"><span data-stu-id="1540e-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="1540e-126">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="1540e-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="1540e-127">Décrit l’instruction `Option Strict`, qui limite les conversions des types de données implicites aux seules conversions étendues, interdit les liaisons tardives et interdit pas le typage implicite qui aboutit à un type `Object`.</span><span class="sxs-lookup"><span data-stu-id="1540e-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
