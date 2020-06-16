---
title: Attribution d'un nom à des ressources
description: Passez en revue les instructions d’affectation de noms pour les ressources dans .NET, qui sont similaires aux instructions relatives aux propriétés d’attribution de noms.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 765337bcf9fad4f9a8c9272a15b5c77d02770471
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768246"
---
# <a name="naming-resources"></a><span data-ttu-id="52bb2-103">Attribution d'un nom à des ressources</span><span class="sxs-lookup"><span data-stu-id="52bb2-103">Naming Resources</span></span>
<span data-ttu-id="52bb2-104">Étant donné que les ressources localisables peuvent être référencées par le biais de certains objets comme s’il s’agissait de propriétés, les instructions d’affectation de noms pour les ressources sont similaires aux instructions de propriété.</span><span class="sxs-lookup"><span data-stu-id="52bb2-104">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="52bb2-105">✔️ Utilisez PascalCasing dans les clés de ressources.</span><span class="sxs-lookup"><span data-stu-id="52bb2-105">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="52bb2-106">✔️ fournissez des identificateurs descriptifs et non courts.</span><span class="sxs-lookup"><span data-stu-id="52bb2-106">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="52bb2-107">❌N’utilisez pas de mots clés spécifiques au langage pour les principaux langages CLR.</span><span class="sxs-lookup"><span data-stu-id="52bb2-107">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="52bb2-108">✔️ Utilisez uniquement des caractères alphanumériques et des traits de soulignement dans les ressources de nommage.</span><span class="sxs-lookup"><span data-stu-id="52bb2-108">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="52bb2-109">✔️ Utilisez la Convention d’affectation de noms suivante pour les ressources de message d’exception.</span><span class="sxs-lookup"><span data-stu-id="52bb2-109">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="52bb2-110">L’identificateur de ressource doit être le nom du type d’exception plus un identificateur abrégé de l’exception :</span><span class="sxs-lookup"><span data-stu-id="52bb2-110">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="52bb2-111">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="52bb2-111">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="52bb2-112">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="52bb2-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="52bb2-113">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="52bb2-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="52bb2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52bb2-114">See also</span></span>

- [<span data-ttu-id="52bb2-115">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="52bb2-115">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="52bb2-116">Instructions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="52bb2-116">Naming Guidelines</span></span>](naming-guidelines.md)
