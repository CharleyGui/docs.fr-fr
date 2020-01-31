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
ms.openlocfilehash: 95aff35569e58eacfd064609140a29b53e0036da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743814"
---
# <a name="naming-resources"></a>Attribution d'un nom à des ressources
Étant donné que les ressources localisables peuvent être référencées par le biais de certains objets comme s’il s’agissait de propriétés, les instructions d’affectation de noms pour les ressources sont similaires aux instructions de propriété.

 ✔️ Utilisez PascalCasing dans les clés de ressources.

 ✔️ fournissez des identificateurs descriptifs et non courts.

 ❌ n’utilisez pas les mots clés spécifiques au langage des principaux langages CLR.

 ✔️ Utilisez uniquement des caractères alphanumériques et des traits de soulignement dans les ressources de nommage.

 ✔️ Utilisez la Convention d’affectation de noms suivante pour les ressources de message d’exception.

 L’identificateur de ressource doit être le nom du type d’exception plus un identificateur abrégé de l’exception :

 `ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`
 `ArgumentExceptionFileNameIsMalformed`

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
