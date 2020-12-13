---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366856"
---
### <a name="exclude-specific-symbols"></a>Exclure des symboles spécifiques

Vous pouvez exclure des symboles spécifiques, tels que des types et des méthodes, de l’analyse. Par exemple, pour spécifier que la règle ne doit pas être exécutée sur un code dans des types nommés `MyType` , ajoutez la paire clé-valeur suivante à un fichier *. editorconfig* dans votre projet :

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

Formats de noms de symboles autorisés dans la valeur de l’option (séparés par `|` ) :

- Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur).
- Noms qualifiés complets dans le format d' [ID de documentation](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)du symbole. Chaque nom de symbole requiert un préfixe de type symbole, tel que `M:` pour les méthodes, `T:` pour les types et `N:` pour les espaces de noms.
- `.ctor` pour les constructeurs et `.cctor` pour les constructeurs statiques.

Exemples :

| Valeur d’option | Résumé |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | Correspond à tous les symboles nommés `MyType` . |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | Correspond à tous les symboles nommés `MyType1` ou `MyType2` . |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | Met en correspondance une méthode spécifique `MyMethod` avec la signature complète spécifiée. |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | Correspond à des méthodes spécifiques `MyMethod1` et `MyMethod2` à des signatures qualifiées complètes respectives. |
