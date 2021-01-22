---
title: Convertir des chaînes en types
description: Comprendre l’analyse des chaînes dans .NET. L’analyse convertit une chaîne représentant un type de base .NET en ce type de base. L’analyse est l’opération inverse de la mise en forme.
ms.date: 03/30/2017
ms.topic: conceptual
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: ff357f8b8225c84e2f6c0e022b269f0ab774dfed
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692849"
---
# <a name="parse-strings-in-net"></a><span data-ttu-id="015c9-105">Analyser des chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="015c9-105">Parse strings in .NET</span></span>

<span data-ttu-id="015c9-106">Une opération d' *analyse* convertit une chaîne qui représente un type de base .net en ce type de base.</span><span class="sxs-lookup"><span data-stu-id="015c9-106">A *parsing* operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="015c9-107">Par exemple, une opération d’analyse est utilisée pour convertir une chaîne en nombre à virgule flottante ou en valeur de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="015c9-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date-and-time value.</span></span> <span data-ttu-id="015c9-108">La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`.</span><span class="sxs-lookup"><span data-stu-id="015c9-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="015c9-109">Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="015c9-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="015c9-110">Tout comme la mise en forme utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour fournir des informations de mise en forme dépendantes de la culture, l’analyse utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour déterminer comment interpréter une représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="015c9-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="015c9-111">Pour plus d’informations, consultez [types de format](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="015c9-111">For more information, see [Format types](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="015c9-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="015c9-112">In This Section</span></span>

 <span data-ttu-id="015c9-113">[Analyse des chaînes numériques](parsing-numeric.md)</span><span class="sxs-lookup"><span data-stu-id="015c9-113">[Parsing Numeric Strings](parsing-numeric.md)</span></span>\
 <span data-ttu-id="015c9-114">Explique comment convertir des chaînes en types numériques .NET.</span><span class="sxs-lookup"><span data-stu-id="015c9-114">Describes how to convert strings into .NET numeric types.</span></span>

 <span data-ttu-id="015c9-115">[Analyse des chaînes de date et d’heure](parsing-datetime.md)</span><span class="sxs-lookup"><span data-stu-id="015c9-115">[Parsing Date and Time Strings](parsing-datetime.md)</span></span>\
 <span data-ttu-id="015c9-116">Explique comment convertir des chaînes en types **DateTime** .NET.</span><span class="sxs-lookup"><span data-stu-id="015c9-116">Describes how to convert strings into .NET **DateTime** types.</span></span>

 <span data-ttu-id="015c9-117">[Analyse d’autres chaînes](parsing-other.md)</span><span class="sxs-lookup"><span data-stu-id="015c9-117">[Parsing Other Strings](parsing-other.md)</span></span>\
 <span data-ttu-id="015c9-118">Explique comment convertir des chaînes en types **Char**, **Boolean** et **Enum**.</span><span class="sxs-lookup"><span data-stu-id="015c9-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>

## <a name="related-sections"></a><span data-ttu-id="015c9-119">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="015c9-119">Related Sections</span></span>

 <span data-ttu-id="015c9-120">[Mise en forme des types](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="015c9-120">[Formatting Types](formatting-types.md)</span></span>\
 <span data-ttu-id="015c9-121">Décrit les concepts de mise en forme de base, tels que les spécificateurs de format et les fournisseurs de format.</span><span class="sxs-lookup"><span data-stu-id="015c9-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>

 <span data-ttu-id="015c9-122">[Conversion de type dans .NET](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="015c9-122">[Type Conversion in .NET](type-conversion.md)</span></span>\
 <span data-ttu-id="015c9-123">Décrit comment convertir des types.</span><span class="sxs-lookup"><span data-stu-id="015c9-123">Describes how to convert types.</span></span>
