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
ms.openlocfilehash: 2ce1b148a2b1605b5b1283bdc3398409661f3f83
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523987"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="4d950-103">Opérations de chaîne de base en .NET</span><span class="sxs-lookup"><span data-stu-id="4d950-103">Basic string operations in .NET</span></span>

<span data-ttu-id="4d950-104">Les applications répondent souvent aux utilisateurs en construisant des messages selon l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d950-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="4d950-105">Par exemple, il n’est pas rare que les sites Web répondent à un utilisateur nouvellement connecté avec un message d’accueil spécialisé qui inclut le nom de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d950-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="4d950-106">Plusieurs méthodes dans les classes <xref:System.String?displayProperty=nameWithType> et <xref:System.Text.StringBuilder?displayProperty=nameWithType> vous permettent de construire de façon dynamique des chaînes personnalisées à afficher dans votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d950-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="4d950-107">Ces méthodes vous aident également à effectuer plusieurs opérations de chaînes de base telles que la création de chaînes à partir de tableaux d’octets, la comparaison des valeurs de chaînes et la modification des chaînes existantes.</span><span class="sxs-lookup"><span data-stu-id="4d950-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4d950-108">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="4d950-108">Related sections</span></span>

<span data-ttu-id="4d950-109">[Conversion de type en .NET](../../../docs/standard/base-types/type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="4d950-109">[Type Conversion in .NET](../../../docs/standard/base-types/type-conversion.md)</span></span>\
<span data-ttu-id="4d950-110">Explique comment convertir un type en un autre.</span><span class="sxs-lookup"><span data-stu-id="4d950-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="4d950-111">[Types de formatage](../../../docs/standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="4d950-111">[Formatting Types](../../../docs/standard/base-types/formatting-types.md)</span></span>\
<span data-ttu-id="4d950-112">Explique comment mettre en forme des chaînes à l’aide de spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="4d950-112">Describes how to format strings using format specifiers.</span></span>
