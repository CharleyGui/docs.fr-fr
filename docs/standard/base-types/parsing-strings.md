---
title: Analyse de chaînes dans .NET
description: Comprendre l’analyse des chaînes dans .NET. L’analyse convertit une chaîne représentant un type de base .NET en ce type de base. L’analyse est l’opération inverse de la mise en forme.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 5e297c8f689fdabc268ee6e269a7969155befe7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769286"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="d699c-105">Analyse de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="d699c-105">Parsing Strings in .NET</span></span>
<span data-ttu-id="d699c-106">Une opération d’analyse convertit une chaîne qui représente un type de base .NET en ce type de base.</span><span class="sxs-lookup"><span data-stu-id="d699c-106">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="d699c-107">Par exemple, une opération d'analyse permet de convertir une chaîne en nombre à virgule flottante ou en valeur de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="d699c-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="d699c-108">La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`.</span><span class="sxs-lookup"><span data-stu-id="d699c-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="d699c-109">Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="d699c-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="d699c-110">Tout comme la mise en forme utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour fournir des informations de mise en forme dépendantes de la culture, l’analyse utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour déterminer comment interpréter une représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="d699c-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="d699c-111">Pour plus d’informations, consultez [Mise en forme des types](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d699c-111">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d699c-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d699c-112">In This Section</span></span>  
 [<span data-ttu-id="d699c-113">Analyse de chaînes numériques</span><span class="sxs-lookup"><span data-stu-id="d699c-113">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="d699c-114">Explique comment convertir des chaînes en types numériques .NET.</span><span class="sxs-lookup"><span data-stu-id="d699c-114">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="d699c-115">Analyse de chaînes de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="d699c-115">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="d699c-116">Explique comment convertir des chaînes en types **DateTime** .NET.</span><span class="sxs-lookup"><span data-stu-id="d699c-116">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="d699c-117">Analyse d'autres chaînes</span><span class="sxs-lookup"><span data-stu-id="d699c-117">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="d699c-118">Explique comment convertir des chaînes en types **Char**, **Boolean** et **Enum**.</span><span class="sxs-lookup"><span data-stu-id="d699c-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d699c-119">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="d699c-119">Related Sections</span></span>  
 [<span data-ttu-id="d699c-120">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="d699c-120">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="d699c-121">Décrit les concepts de mise en forme de base, tels que les spécificateurs de format et les fournisseurs de format.</span><span class="sxs-lookup"><span data-stu-id="d699c-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="d699c-122">Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="d699c-122">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="d699c-123">Décrit comment convertir des types.</span><span class="sxs-lookup"><span data-stu-id="d699c-123">Describes how to convert types.</span></span>
