---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97532046"
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
