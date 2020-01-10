---
title: Attribution d'un nom à des ressources
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: b64a3ef6e12f8ea1abf7efd9c22f2f4333dda5c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709164"
---
# <a name="naming-resources"></a><span data-ttu-id="6e562-102">Attribution d'un nom à des ressources</span><span class="sxs-lookup"><span data-stu-id="6e562-102">Naming Resources</span></span>
<span data-ttu-id="6e562-103">Étant donné que les ressources localisables peuvent être référencées par le biais de certains objets comme s’il s’agissait de propriétés, les instructions d’affectation de noms pour les ressources sont similaires aux instructions de propriété.</span><span class="sxs-lookup"><span data-stu-id="6e562-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="6e562-104">**✓ DO** utilisent la casse Pascal dans les clés de ressources.</span><span class="sxs-lookup"><span data-stu-id="6e562-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="6e562-105">**✓ DO** fournir descriptif au lieu d’identificateurs courts.</span><span class="sxs-lookup"><span data-stu-id="6e562-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="6e562-106">**X DO NOT** utiliser des mots clés de langage spécifique langage CLR principal.</span><span class="sxs-lookup"><span data-stu-id="6e562-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="6e562-107">**✓ DO** utiliser uniquement des caractères alphanumériques et des traits de soulignement dans les noms des ressources.</span><span class="sxs-lookup"><span data-stu-id="6e562-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="6e562-108">**✓ DO** utilisent la convention d’affectation de noms suivante pour les ressources de message d’exception.</span><span class="sxs-lookup"><span data-stu-id="6e562-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="6e562-109">L’identificateur de ressource doit être le nom du type d’exception plus un identificateur abrégé de l’exception :</span><span class="sxs-lookup"><span data-stu-id="6e562-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="6e562-110">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="6e562-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6e562-111">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6e562-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e562-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e562-112">See also</span></span>

- [<span data-ttu-id="6e562-113">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6e562-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="6e562-114">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="6e562-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
