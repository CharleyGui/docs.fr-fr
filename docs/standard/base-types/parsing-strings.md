---
title: Analyse de chaînes dans .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084315"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="0ee37-102">Analyse de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="0ee37-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="0ee37-103">Une opération d’analyse convertit une chaîne qui représente un type de base .NET en ce type de base.</span><span class="sxs-lookup"><span data-stu-id="0ee37-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="0ee37-104">Par exemple, une opération d'analyse permet de convertir une chaîne en nombre à virgule flottante ou en valeur de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="0ee37-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="0ee37-105">La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`.</span><span class="sxs-lookup"><span data-stu-id="0ee37-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="0ee37-106">Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="0ee37-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="0ee37-107">Tout comme la mise en forme utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour fournir des informations de mise en forme dépendantes de la culture, l’analyse utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour déterminer comment interpréter une représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="0ee37-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="0ee37-108">Pour plus d’informations, consultez [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="0ee37-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ee37-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0ee37-109">In This Section</span></span>  
 [<span data-ttu-id="0ee37-110">Parsing Chaînes numériques</span><span class="sxs-lookup"><span data-stu-id="0ee37-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="0ee37-111">Explique comment convertir des chaînes en types numériques .NET.</span><span class="sxs-lookup"><span data-stu-id="0ee37-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="0ee37-112">Analyse des chaînes de date et d'heure</span><span class="sxs-lookup"><span data-stu-id="0ee37-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="0ee37-113">Explique comment convertir des chaînes en types **DateTime** .NET.</span><span class="sxs-lookup"><span data-stu-id="0ee37-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="0ee37-114">Analyse d'autres chaînes</span><span class="sxs-lookup"><span data-stu-id="0ee37-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="0ee37-115">Explique comment convertir des chaînes en types **Char**, **Boolean** et **Enum**.</span><span class="sxs-lookup"><span data-stu-id="0ee37-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0ee37-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0ee37-116">Related Sections</span></span>  
 [<span data-ttu-id="0ee37-117">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="0ee37-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="0ee37-118">Décrit les concepts de mise en forme de base, tels que les spécificateurs de format et les fournisseurs de format.</span><span class="sxs-lookup"><span data-stu-id="0ee37-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="0ee37-119">Conversion de types dans .NET</span><span class="sxs-lookup"><span data-stu-id="0ee37-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="0ee37-120">Décrit comment convertir des types.</span><span class="sxs-lookup"><span data-stu-id="0ee37-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="0ee37-121">Base Types</span><span class="sxs-lookup"><span data-stu-id="0ee37-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="0ee37-122">Décrit les opérations courantes que vous pouvez effectuer sur les types de base .NET.</span><span class="sxs-lookup"><span data-stu-id="0ee37-122">Describes common operations that you can perform on .NET base types.</span></span>
