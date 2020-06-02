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
ms.openlocfilehash: 8c19f6bcbdf5e4829c91aee1e2fd631537ed2e0a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277750"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="d2835-103">Opérations de chaînes de base dans .NET</span><span class="sxs-lookup"><span data-stu-id="d2835-103">Basic string operations in .NET</span></span>

<span data-ttu-id="d2835-104">Les applications répondent souvent aux utilisateurs en construisant des messages selon l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2835-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="d2835-105">Par exemple, il n’est pas rare pour les sites Web de répondre à un utilisateur qui vient d’être connecté avec un message d’accueil spécialisé qui comprend le nom de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2835-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="d2835-106">Plusieurs méthodes dans les classes <xref:System.String?displayProperty=nameWithType> et <xref:System.Text.StringBuilder?displayProperty=nameWithType> vous permettent de construire de façon dynamique des chaînes personnalisées à afficher dans votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2835-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="d2835-107">Ces méthodes vous aident également à effectuer plusieurs opérations de chaînes de base telles que la création de chaînes à partir de tableaux d’octets, la comparaison des valeurs de chaînes et la modification des chaînes existantes.</span><span class="sxs-lookup"><span data-stu-id="d2835-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d2835-108">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="d2835-108">Related sections</span></span>

<span data-ttu-id="d2835-109">[Conversion de type dans .NET](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="d2835-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="d2835-110">Explique comment convertir un type en un autre.</span><span class="sxs-lookup"><span data-stu-id="d2835-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="d2835-111">[Mise en forme des types](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="d2835-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="d2835-112">Explique comment mettre en forme des chaînes à l’aide de spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="d2835-112">Describes how to format strings using format specifiers.</span></span>
