---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366856"
---
### <a name="exclude-specific-symbols"></a><span data-ttu-id="c85ce-101">Exclure des symboles spécifiques</span><span class="sxs-lookup"><span data-stu-id="c85ce-101">Exclude specific symbols</span></span>

<span data-ttu-id="c85ce-102">Vous pouvez exclure des symboles spécifiques, tels que des types et des méthodes, de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="c85ce-102">You can exclude specific symbols, such as types and methods, from analysis.</span></span> <span data-ttu-id="c85ce-103">Par exemple, pour spécifier que la règle ne doit pas être exécutée sur un code dans des types nommés `MyType` , ajoutez la paire clé-valeur suivante à un fichier *. editorconfig* dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="c85ce-103">For example, to specify that the rule should not run on any code within types named `MyType`, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

<span data-ttu-id="c85ce-104">Formats de noms de symboles autorisés dans la valeur de l’option (séparés par `|` ) :</span><span class="sxs-lookup"><span data-stu-id="c85ce-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="c85ce-105">Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur).</span><span class="sxs-lookup"><span data-stu-id="c85ce-105">Symbol name only (includes all symbols with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="c85ce-106">Noms qualifiés complets dans le format d' [ID de documentation](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)du symbole.</span><span class="sxs-lookup"><span data-stu-id="c85ce-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings).</span></span> <span data-ttu-id="c85ce-107">Chaque nom de symbole requiert un préfixe de type symbole, tel que `M:` pour les méthodes, `T:` pour les types et `N:` pour les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="c85ce-107">Each symbol name requires a symbol-kind prefix, such as `M:` for methods, `T:` for types, and `N:` for namespaces.</span></span>
- <span data-ttu-id="c85ce-108">`.ctor` pour les constructeurs et `.cctor` pour les constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="c85ce-108">`.ctor` for constructors and `.cctor` for static constructors.</span></span>

<span data-ttu-id="c85ce-109">Exemples :</span><span class="sxs-lookup"><span data-stu-id="c85ce-109">Examples:</span></span>

| <span data-ttu-id="c85ce-110">Valeur d’option</span><span class="sxs-lookup"><span data-stu-id="c85ce-110">Option Value</span></span> | <span data-ttu-id="c85ce-111">Résumé</span><span class="sxs-lookup"><span data-stu-id="c85ce-111">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | <span data-ttu-id="c85ce-112">Correspond à tous les symboles nommés `MyType` .</span><span class="sxs-lookup"><span data-stu-id="c85ce-112">Matches all symbols named `MyType`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | <span data-ttu-id="c85ce-113">Correspond à tous les symboles nommés `MyType1` ou `MyType2` .</span><span class="sxs-lookup"><span data-stu-id="c85ce-113">Matches all symbols named either `MyType1` or `MyType2`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | <span data-ttu-id="c85ce-114">Met en correspondance une méthode spécifique `MyMethod` avec la signature complète spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c85ce-114">Matches specific method `MyMethod` with the specified fully qualified signature.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | <span data-ttu-id="c85ce-115">Correspond à des méthodes spécifiques `MyMethod1` et `MyMethod2` à des signatures qualifiées complètes respectives.</span><span class="sxs-lookup"><span data-stu-id="c85ce-115">Matches specific methods `MyMethod1` and `MyMethod2` with the respective fully qualified signatures.</span></span> |
