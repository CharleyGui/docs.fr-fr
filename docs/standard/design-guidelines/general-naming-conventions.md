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
ms.openlocfilehash: ef4a8f571a67477739bbc59d3103ba78dea47177
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635920"
---
# <a name="general-naming-conventions"></a>Conventions générales d'affectation de noms

Cette section décrit les conventions générales de nommage qui se rapportent au choix des mots, les lignes directrices sur l’utilisation d’abréviations et d’acronymes, et des recommandations sur la façon d’éviter d’utiliser des noms spécifiques à la langue.

## <a name="word-choice"></a>Choix de mots
 ✔️ NE choisissez facilement lisible noms d’identification.

 Par exemple, une `HorizontalAlignment` propriété nommée est `AlignmentHorizontal`plus lisible en anglais que .

 ✔️ ne favorisent la lisibilité sur la brièveté.

 Le nom `CanScrollHorizontally` de `ScrollableX` la propriété est meilleur que (une référence obscure à l’axe X).

 ❌NE PAS utiliser les soulignements, les traits d’union, ou tout autre caractère non anphanumérique.

 ❌NE PAS utiliser la notation hongroise.

 ❌AVOID à l’aide d’identifiants qui entrent en conflit avec les mots clés des langages de programmation largement utilisés.

 Conformément à la règle 4 de la spécification linguistique commune (CLS), toutes les langues conformes doivent fournir un mécanisme qui permet l’accès à des éléments nommés qui utilisent un mot clé de cette langue comme identifiant. C, par exemple, utilise le signe de l’inscription comme mécanisme d’évacuation dans ce cas. Cependant, il est toujours une bonne idée d’éviter les mots clés communs, car il est beaucoup plus difficile d’utiliser une méthode avec la séquence d’évacuation que l’un sans elle.

## <a name="using-abbreviations-and-acronyms"></a>Utilisation d’abréviations et d’acronymes
 ❌NE PAS utiliser d’abréviations ou de contractions dans le cadre de noms d’identifiants.

 Par exemple, `GetWindow` utiliser `GetWin`plutôt que .

 ❌NE PAS utiliser les acronymes qui ne sont pas largement acceptés, et même si elles sont, seulement si nécessaire.

## <a name="avoiding-language-specific-names"></a>Éviter les noms spécifiques à la langue
 ✔️ NE pas utiliser des noms sémantically intéressants plutôt que des mots clés spécifiques à la langue pour les noms de type.

 Par exemple, `GetLength` est un `GetInt`meilleur nom que .

 ✔️ NE pas utiliser un nom générique de type CLR, plutôt que d’un nom spécifique à la langue, dans les rares cas où un identifiant n’a pas de signification sémantique au-delà de son type.

 Par exemple, une méthode <xref:System.Int64> de `ToInt64`conversion `ToLong` en <xref:System.Int64> devrait être nommée , non pas `long`(parce qu’est un nom CLR pour l’alias spécifique à la C). Le tableau suivant présente plusieurs types de données de base à l’aide des noms de type CLR (ainsi que les noms de type correspondants pour le C, Visual Basic et le CMD).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**Sbyte**|**char**|**Sbyte**|
|**byte**|**Octet**|**unsigned char**|**Octet**|
|**short**|**Court**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**Int**|**Integer**|**Int**|**Int32**|
|**uint**|**UInt32**|**nombre entier non signé**|**UInt32**|
|**long**|**Long**|**__int64**|**Int64**|
|**Ulong**|**UInt64**|**unsigned __int64**|**UInt64**|
|**float**|**Seul**|**float**|**Seul**|
|**double**|**Double**|**double**|**Double**|
|**bool**|**Boolean**|**bool**|**Boolean**|
|**char**|**Char Char**|**Wchar_t**|**Char Char**|
|**string**|**Chaîne**|**Chaîne**|**Chaîne**|
|**Objet**|**Object**|**Object**|**Object**|

 ✔️ N’utilisez pas un nom `value` commun, tel que ou, `item`plutôt que de répéter le nom de type, dans les rares cas où un identifiant n’a pas de signification sémantique et le type de paramètre n’est pas important.

## <a name="naming-new-versions-of-existing-apis"></a>Nommer de nouvelles versions des API existantes
 ✔️ UTILISEZ un nom similaire à l’ancienne API lors de la création de nouvelles versions d’une API existante.

 Cela permet de mettre en évidence la relation entre les API.

 ✔️ NE préfèrent ajouter un suffixe plutôt qu’un préfixe pour indiquer une nouvelle version d’une API existante.

 Cela facilitera la découverte lors de la navigation de la documentation, ou en utilisant IntelliSense. L’ancienne version de l’API sera organisée à proximité des nouvelles API, car la plupart des navigateurs et IntelliSense montrent des identifiants par ordre alphabétique.

 ✔️ CONSIDER à l’aide d’un identifiant tout neuf, mais significatif, au lieu d’ajouter un suffixe ou un préfixe.

 ✔️ utilisez un suffixe numérique pour indiquer une nouvelle version d’une API existante, en particulier si le nom existant de l’API est le seul nom qui a du sens (c.-à-d. s’il s’agit d’une norme de l’industrie) et si l’ajout d’un suffixe significatif (ou changer le nom) n’est pas une option appropriée.

 ❌NE PAS utiliser le suffixe "Ex" (ou un autre) pour un identifiant afin de le distinguer d’une version antérieure de la même API.

 ✔️ UTILISEZ le suffixe "64" lors de l’introduction de versions d’API qui fonctionnent sur un intégriste 64 bits (un long intégriste) au lieu d’un intégriste 32 bits. Vous n’avez qu’à adopter cette approche lorsque l’API 32 bits existant existe; ne le faites pas pour les API flambant neufs avec seulement une version 64 bits.

 *Portions &copy; 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception du .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
- [Conventions de nommage .NET pour EditorConfig](/visualstudio/ide/editorconfig-naming-conventions)
