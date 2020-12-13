---
ms.openlocfilehash: 150882f3e4c9ff7abe811e09da94b8141de75778
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366831"
---
### <a name="exclude-specific-types-and-their-derived-types"></a>Exclure des types spécifiques et leurs types dérivés

Vous pouvez exclure des types spécifiques et leurs types dérivés de l’analyse. Par exemple, pour spécifier que la règle ne doit pas s’exécuter sur les méthodes dans les types nommés `MyType` et leurs types dérivés, ajoutez la paire clé-valeur suivante à un fichier *. editorconfig* dans votre projet :

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

Formats de noms de symboles autorisés dans la valeur de l’option (séparés par `|` ) :

- Nom de type uniquement (comprend tous les types portant le nom, quel que soit le type ou l’espace de noms conteneur).
- Noms qualifiés complets dans le format d' [ID de documentation](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)du symbole, avec un `T:` préfixe facultatif.

Exemples :

| Valeur d’option | Résumé |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | Correspond à tous les types nommés `MyType` et tous leurs types dérivés. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | Correspond à tous les types nommés, `MyType1` ou `MyType2` et tous leurs types dérivés. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | Correspond à un type spécifique `MyType` avec le nom qualifié complet donné et tous ses types dérivés. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | Correspond à des types spécifiques `MyType1` et `MyType2` aux noms qualifiés complets respectifs, ainsi qu’à tous leurs types dérivés. |
