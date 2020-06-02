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
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277412"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="a8f81-102">Analyse de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="a8f81-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="a8f81-103">Une opération d’analyse convertit une chaîne qui représente un type de base .NET en ce type de base.</span><span class="sxs-lookup"><span data-stu-id="a8f81-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="a8f81-104">Par exemple, une opération d'analyse permet de convertir une chaîne en nombre à virgule flottante ou en valeur de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="a8f81-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="a8f81-105">La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`.</span><span class="sxs-lookup"><span data-stu-id="a8f81-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="a8f81-106">Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="a8f81-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="a8f81-107">Tout comme la mise en forme utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour fournir des informations de mise en forme dépendantes de la culture, l’analyse utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour déterminer comment interpréter une représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="a8f81-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="a8f81-108">Pour plus d’informations, consultez [Mise en forme des types](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="a8f81-108">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8f81-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a8f81-109">In This Section</span></span>  
 [<span data-ttu-id="a8f81-110">Analyse de chaînes numériques</span><span class="sxs-lookup"><span data-stu-id="a8f81-110">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="a8f81-111">Explique comment convertir des chaînes en types numériques .NET.</span><span class="sxs-lookup"><span data-stu-id="a8f81-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="a8f81-112">Analyse de chaînes de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="a8f81-112">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="a8f81-113">Explique comment convertir des chaînes en types **DateTime** .NET.</span><span class="sxs-lookup"><span data-stu-id="a8f81-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="a8f81-114">Analyse d'autres chaînes</span><span class="sxs-lookup"><span data-stu-id="a8f81-114">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="a8f81-115">Explique comment convertir des chaînes en types **Char**, **Boolean** et **Enum**.</span><span class="sxs-lookup"><span data-stu-id="a8f81-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8f81-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="a8f81-116">Related Sections</span></span>  
 [<span data-ttu-id="a8f81-117">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="a8f81-117">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="a8f81-118">Décrit les concepts de mise en forme de base, tels que les spécificateurs de format et les fournisseurs de format.</span><span class="sxs-lookup"><span data-stu-id="a8f81-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="a8f81-119">Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="a8f81-119">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="a8f81-120">Décrit comment convertir des types.</span><span class="sxs-lookup"><span data-stu-id="a8f81-120">Describes how to convert types.</span></span>
