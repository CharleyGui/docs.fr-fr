---
title: Conventions générales d'affectation de noms
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: f8576790a2be08c623807e236d156e0e7f93dd14
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741591"
---
# <a name="general-naming-conventions"></a>Conventions générales d'affectation de noms
Cette section décrit les conventions d’affectation de noms générales relatives au choix de mots, des instructions sur l’utilisation des abréviations et des acronymes, ainsi que des recommandations sur la façon d’éviter d’utiliser des noms spécifiques à une langue.

## <a name="word-choice"></a>Choix de mots
 ✔️ Choisissez des noms d’identificateur facilement lisibles.

 Par exemple, une propriété nommée `HorizontalAlignment` est plus lisible que `AlignmentHorizontal`.

 ✔️ préférez la lisibilité par rapport à la concision.

 Le nom de la propriété `CanScrollHorizontally` est mieux que `ScrollableX` (une référence obscurcie à l’axe X).

 ❌ n’utilisez pas de traits de soulignement, de traits d’Union ou tout autre caractère non alphanumérique.

 ❌ n’utilisez pas la notation hongroise.

 ❌ éviter d’utiliser des identificateurs qui sont en conflit avec des mots clés de langages de programmation largement utilisés.

 Conformément à la règle 4 du Common Language Specification (CLS), tous les langages conformes doivent fournir un mécanisme qui permet d’accéder à des éléments nommés qui utilisent un mot clé de ce langage comme identificateur. C#, par exemple, utilise le signe @ comme mécanisme d’échappement dans ce cas. Toutefois, il est toujours judicieux d’éviter les mots clés courants, car il est bien plus difficile d’utiliser une méthode avec la séquence d’échappement que l’autre sans lui.

## <a name="using-abbreviations-and-acronyms"></a>Utilisation des abréviations et des acronymes
 ❌ n’utilisez pas d’abréviations ou de contractions dans le cadre des noms d’identificateur.

 Par exemple, utilisez `GetWindow` plutôt que `GetWin`.

 ❌ n’utilisez pas les acronymes qui ne sont pas largement acceptés, et même s’ils le sont, uniquement lorsque cela est nécessaire.

## <a name="avoiding-language-specific-names"></a>Éviter les noms spécifiques à une langue
 ✔️ Utilisez des noms sémantiquement intéressants plutôt que des mots clés spécifiques à une langue pour les noms de types.

 Par exemple, `GetLength` est un nom plus approprié que `GetInt`.

 ✔️ Utilisez un nom de type CLR générique, plutôt qu’un nom propre au langage, dans les rares cas où un identificateur n’a aucune signification sémantique au-delà de son type.

 Par exemple, une méthode qui est convertie en <xref:System.Int64> doit être nommée `ToInt64`, et non `ToLong` (car <xref:System.Int64> est C#un nom CLR pour l’alias spécifique à, `long`). Le tableau suivant présente plusieurs types de données de base utilisant les noms de type CLR (ainsi que les noms de C#types correspondants pour, C++Visual Basic et).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**SByte**|**char**|**SByte**|
|**byte**|**Byte**|**unsigned char**|**Byte**|
|**short**|**short**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**Integer**|**int**|**Int32**|
|**uint**|**UInt32**|**unsigned int**|**UInt32**|
|**long**|**Long**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|
|**float**|**Single**|**float**|**Single**|
|**double**|**Double**|**double**|**Double**|
|**bool**|**Boolean**|**bool**|**Boolean**|
|**char**|**Char**|**wchar_t**|**Char**|
|**string**|**String**|**String**|**String**|
|**object**|**Objet**|**Objet**|**Objet**|

 ✔️ Utilisez un nom commun, tel que `value` ou `item`, au lieu de répéter le nom de type, dans les rares cas où un identificateur n’a aucune signification sémantique et que le type du paramètre n’est pas important.

## <a name="naming-new-versions-of-existing-apis"></a>Attribution de noms aux nouvelles versions des API existantes
 ✔️ Utilisez un nom similaire à l’ancienne API lors de la création de nouvelles versions d’une API existante.

 Cela permet de mettre en évidence la relation entre les API.

 ✔️ préférez ajouter un suffixe plutôt qu’un préfixe pour indiquer une nouvelle version d’une API existante.

 Cela aidera la découverte lors de la navigation dans la documentation ou à l’aide d’IntelliSense. L’ancienne version de l’API sera organisée à proximité des nouvelles API, car la plupart des navigateurs et IntelliSense affichent des identificateurs dans l’ordre alphabétique.

 ✔️ envisagez d’utiliser un nouvel identificateur, mais explicite, au lieu d’ajouter un suffixe ou un préfixe.

 ✔️ Utilisez un suffixe numérique pour indiquer une nouvelle version d’une API existante, en particulier si le nom existant de l’API est le seul nom qui est pertinent (c’est-à-dire, s’il s’agit d’une norme industrielle) et si l’ajout d’un suffixe significatif (ou la modification du nom) n’est pas un Opti approprié sur.

 ❌ n’utilisez pas le suffixe « ex » (ou un suffixe similaire) pour un identificateur pour le distinguer d’une version antérieure de la même API.

 ✔️ Utilisez le suffixe « 64 » lors de l’introduction de versions d’API qui fonctionnent sur un entier 64 bits (entier long) au lieu d’un entier de 32 bits. Vous devez adopter cette approche uniquement lorsque l’API 32 bits existante existe. ne le faites pas pour les nouvelles API avec une version 64 bits uniquement.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
