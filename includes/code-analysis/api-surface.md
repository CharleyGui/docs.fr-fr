---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "97700856"
---
### <a name="include-specific-api-surfaces"></a><span data-ttu-id="9c96c-101">Inclure des surfaces d’API spécifiques</span><span class="sxs-lookup"><span data-stu-id="9c96c-101">Include specific API surfaces</span></span>

<span data-ttu-id="9c96c-102">Vous pouvez configurer les parties de votre code base pour exécuter cette règle, en fonction de leur accessibilité.</span><span class="sxs-lookup"><span data-stu-id="9c96c-102">You can configure which parts of your codebase to run this rule on, based on their accessibility.</span></span> <span data-ttu-id="9c96c-103">Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier *. editorconfig* dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="9c96c-103">For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
