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
ms.openlocfilehash: c90987fd28d5157cfb7f7eea4680b5ab4be1a200
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290952"
---
# <a name="general-naming-conventions"></a>Conventions générales d'affectation de noms

Cette section décrit les conventions d’affectation de noms générales relatives au choix de mots, des instructions sur l’utilisation des abréviations et des acronymes, ainsi que des recommandations sur la façon d’éviter d’utiliser des noms spécifiques à une langue.

## <a name="word-choice"></a>Choix de mots
 ✔️ Choisissez des noms d’identificateur facilement lisibles.

 Par exemple, une propriété nommée `HorizontalAlignment` est plus lisible en anglais que `AlignmentHorizontal` .

 ✔️ préférez la lisibilité par rapport à la concision.

 Le nom de la propriété `CanScrollHorizontally` est mieux que `ScrollableX` (une référence cachée à l’axe X).

 ❌N’utilisez pas de traits de soulignement, de traits d’Union ou tout autre caractère non alphanumérique.

 ❌N’utilisez pas la notation hongroise.

 ❌Évitez d’utiliser des identificateurs qui sont en conflit avec des mots clés de langages de programmation largement utilisés.

 Conformément à la règle 4 du Common Language Specification (CLS), tous les langages conformes doivent fournir un mécanisme qui permet d’accéder à des éléments nommés qui utilisent un mot clé de ce langage comme identificateur. C#, par exemple, utilise le signe @ comme mécanisme d’échappement dans ce cas. Toutefois, il est toujours judicieux d’éviter les mots clés courants, car il est bien plus difficile d’utiliser une méthode avec la séquence d’échappement que l’autre sans lui.

## <a name="using-abbreviations-and-acronyms"></a>Utilisation des abréviations et des acronymes
 ❌N’utilisez pas d’abréviations ou de contractions dans les noms d’identificateurs.

 Par exemple, utilisez `GetWindow` plutôt que `GetWin` .

 ❌N’utilisez pas les acronymes qui ne sont pas largement acceptés, et même s’ils le sont, uniquement lorsque cela est nécessaire.

## <a name="avoiding-language-specific-names"></a>Éviter les noms spécifiques à une langue
 ✔️ Utilisez des noms sémantiquement intéressants plutôt que des mots clés spécifiques à une langue pour les noms de types.

 Par exemple, `GetLength` est un meilleur nom que `GetInt` .

 ✔️ Utilisez un nom de type CLR générique, plutôt qu’un nom propre au langage, dans les rares cas où un identificateur n’a aucune signification sémantique au-delà de son type.

 Par exemple, une méthode qui est convertie en <xref:System.Int64> doit être nommée `ToInt64` , et non `ToLong` (car <xref:System.Int64> est un nom CLR pour l’alias spécifique à C# `long` ). Le tableau suivant présente plusieurs types de données de base à l’aide des noms de types CLR (ainsi que des noms de types correspondants pour C#, Visual Basic et C++).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**SByte**|**char**|**SByte**|
|**byte**|**Poids**|**unsigned char**|**Poids**|
|**Résumé**|**Court**|**Résumé**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**Integer**|**int**|**Int32**|
|**uint**|**UInt32**|**nombre entier non signé**|**UInt32**|
|**long**|**Long**|**__int64**|**Int64**|
|**correspondante**|**UInt64**|**unsigned __int64**|**UInt64**|
|**float**|**Unique**|**float**|**Unique**|
|**double**|**Cliquer**|**double**|**Cliquer**|
|**bool**|**Booléen**|**bool**|**Booléen**|
|**char**|**Char**|**wchar_t**|**Char**|
|**string**|**Chaîne**|**Chaîne**|**Chaîne**|
|**object**|**Objet**|**Objet**|**Objet**|

 ✔️ Utilisez un nom commun, tel que `value` ou `item` , au lieu de répéter le nom de type, dans les rares cas où un identificateur n’a aucune signification sémantique et que le type du paramètre n’est pas important.

## <a name="naming-new-versions-of-existing-apis"></a>Attribution de noms aux nouvelles versions des API existantes
 ✔️ Utilisez un nom similaire à l’ancienne API lors de la création de nouvelles versions d’une API existante.

 Cela permet de mettre en évidence la relation entre les API.

 ✔️ préférez ajouter un suffixe plutôt qu’un préfixe pour indiquer une nouvelle version d’une API existante.

 Cela aidera la découverte lors de la navigation dans la documentation ou à l’aide d’IntelliSense. L’ancienne version de l’API sera organisée à proximité des nouvelles API, car la plupart des navigateurs et IntelliSense affichent des identificateurs dans l’ordre alphabétique.

 ✔️ envisagez d’utiliser un nouvel identificateur, mais explicite, au lieu d’ajouter un suffixe ou un préfixe.

 ✔️ Utilisez un suffixe numérique pour indiquer une nouvelle version d’une API existante, en particulier si le nom existant de l’API est le seul nom pertinent (c’est-à-dire, s’il s’agit d’une norme industrielle) et si l’ajout d’un suffixe significatif (ou la modification du nom) n’est pas une option appropriée.

 ❌N’utilisez pas le suffixe « ex » (ou un suffixe similaire) pour un identificateur pour le distinguer d’une version antérieure de la même API.

 ✔️ Utilisez le suffixe « 64 » lors de l’introduction de versions d’API qui fonctionnent sur un entier 64 bits (entier long) au lieu d’un entier de 32 bits. Vous devez adopter cette approche uniquement lorsque l’API 32 bits existante existe. ne le faites pas pour les nouvelles API avec une version 64 bits uniquement.

 *Parties &copy; 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception du .NET Framework](index.md)
- [Instructions de nommage](naming-guidelines.md)
- [Conventions de nommage .NET pour EditorConfig](/visualstudio/ide/editorconfig-naming-conventions)
