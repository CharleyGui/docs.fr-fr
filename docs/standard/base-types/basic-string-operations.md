---
title: Opérations de chaînes de base dans .NET
description: Découvrez plus en détail les opérations de base que vous pouvez effectuer sur les chaînes.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 05cdf399e104fc9e528c954adb19634a5c136664
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132910"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="aac52-103">Opérations de chaînes de base dans .NET</span><span class="sxs-lookup"><span data-stu-id="aac52-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="aac52-104">Les applications répondent souvent aux utilisateurs en construisant des messages selon l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aac52-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="aac52-105">Par exemple, il n’est pas rare pour les sites web de répondre à un utilisateur qui vient de se connecter par un message d’accueil spécialisé qui inclut le nom de cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aac52-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="aac52-106">Plusieurs méthodes dans les classes <xref:System.String?displayProperty=nameWithType> et <xref:System.Text.StringBuilder?displayProperty=nameWithType> vous permettent de construire de façon dynamique des chaînes personnalisées à afficher dans votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aac52-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="aac52-107">Ces méthodes vous aident également à effectuer plusieurs opérations de chaînes de base telles que la création de chaînes à partir de tableaux d’octets, la comparaison des valeurs de chaînes et la modification des chaînes existantes.</span><span class="sxs-lookup"><span data-stu-id="aac52-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aac52-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="aac52-108">In This Section</span></span>  
 [<span data-ttu-id="aac52-109">Création de nouvelles chaînes</span><span class="sxs-lookup"><span data-stu-id="aac52-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="aac52-110">Décrit les méthodes de base pour convertir des objets en chaînes et combiner des chaînes.</span><span class="sxs-lookup"><span data-stu-id="aac52-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="aac52-111">Suppression d’espaces et de caractères</span><span class="sxs-lookup"><span data-stu-id="aac52-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="aac52-112">Décrit la manière de supprimer des caractères dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="aac52-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="aac52-113">Cordages de rembourrage</span><span class="sxs-lookup"><span data-stu-id="aac52-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="aac52-114">Décrit comment insérer des caractères ou des espaces vides dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="aac52-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="aac52-115">Comparaison de chaînes</span><span class="sxs-lookup"><span data-stu-id="aac52-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="aac52-116">Décrit la manière de comparer le contenu de deux chaînes ou plus.</span><span class="sxs-lookup"><span data-stu-id="aac52-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="aac52-117">Cas changeant</span><span class="sxs-lookup"><span data-stu-id="aac52-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="aac52-118">Décrit la manière de modifier la casse des caractères dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="aac52-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="aac52-119">Utilisation de la classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="aac52-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="aac52-120">Explique comment créer et modifier des objets string dynamiques avec la classe <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="aac52-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="aac52-121">Guide pratique pour effectuer des manipulations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="aac52-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="aac52-122">Décrit l’utilisation des opérations de chaînes de base.</span><span class="sxs-lookup"><span data-stu-id="aac52-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aac52-123">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="aac52-123">Related Sections</span></span>  
 [<span data-ttu-id="aac52-124">Conversion de types dans .NET</span><span class="sxs-lookup"><span data-stu-id="aac52-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="aac52-125">Explique comment convertir un type en un autre.</span><span class="sxs-lookup"><span data-stu-id="aac52-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="aac52-126">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="aac52-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="aac52-127">Explique comment mettre en forme des chaînes à l’aide de spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="aac52-127">Describes how to format strings using format specifiers.</span></span>
