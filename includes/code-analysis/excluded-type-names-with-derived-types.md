---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97532046"
---
### <a name="exclude-specific-types-and-their-derived-types"></a><span data-ttu-id="d84ec-101">Exclure des types spécifiques et leurs types dérivés</span><span class="sxs-lookup"><span data-stu-id="d84ec-101">Exclude specific types and their derived types</span></span>

<span data-ttu-id="d84ec-102">Vous pouvez exclure des types spécifiques et leurs types dérivés de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="d84ec-102">You can exclude specific types and their derived types from analysis.</span></span> <span data-ttu-id="d84ec-103">Par exemple, pour spécifier que la règle ne doit pas s’exécuter sur les méthodes dans les types nommés `MyType` et leurs types dérivés, ajoutez la paire clé-valeur suivante à un fichier *. editorconfig* dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="d84ec-103">For example, to specify that the rule should not run on any methods within types named `MyType` and their derived types, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

<span data-ttu-id="d84ec-104">Formats de noms de symboles autorisés dans la valeur de l’option (séparés par `|` ) :</span><span class="sxs-lookup"><span data-stu-id="d84ec-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="d84ec-105">Nom de type uniquement (comprend tous les types portant le nom, quel que soit le type ou l’espace de noms conteneur).</span><span class="sxs-lookup"><span data-stu-id="d84ec-105">Type name only (includes all types with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="d84ec-106">Noms qualifiés complets dans le format d' [ID de documentation](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)du symbole, avec un `T:` préfixe facultatif.</span><span class="sxs-lookup"><span data-stu-id="d84ec-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), with an optional `T:` prefix.</span></span>

<span data-ttu-id="d84ec-107">Exemples :</span><span class="sxs-lookup"><span data-stu-id="d84ec-107">Examples:</span></span>

| <span data-ttu-id="d84ec-108">Valeur d’option</span><span class="sxs-lookup"><span data-stu-id="d84ec-108">Option Value</span></span> | <span data-ttu-id="d84ec-109">Résumé</span><span class="sxs-lookup"><span data-stu-id="d84ec-109">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | <span data-ttu-id="d84ec-110">Correspond à tous les types nommés `MyType` et tous leurs types dérivés.</span><span class="sxs-lookup"><span data-stu-id="d84ec-110">Matches all types named `MyType` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | <span data-ttu-id="d84ec-111">Correspond à tous les types nommés, `MyType1` ou `MyType2` et tous leurs types dérivés.</span><span class="sxs-lookup"><span data-stu-id="d84ec-111">Matches all types named either `MyType1` or `MyType2` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | <span data-ttu-id="d84ec-112">Correspond à un type spécifique `MyType` avec le nom qualifié complet donné et tous ses types dérivés.</span><span class="sxs-lookup"><span data-stu-id="d84ec-112">Matches specific type `MyType` with given fully qualified name and all of its derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | <span data-ttu-id="d84ec-113">Correspond à des types spécifiques `MyType1` et `MyType2` aux noms qualifiés complets respectifs, ainsi qu’à tous leurs types dérivés.</span><span class="sxs-lookup"><span data-stu-id="d84ec-113">Matches specific types `MyType1` and `MyType2` with the respective fully qualified names, and all of their derived types.</span></span> |