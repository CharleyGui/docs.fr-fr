---
ms.openlocfilehash: b26e346f7076a57aef8ae7587ab1222b4100a323
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957934"
---
## <a name="suppress-a-warning"></a><span data-ttu-id="27af8-101">Supprimer un avertissement</span><span class="sxs-lookup"><span data-stu-id="27af8-101">Suppress a warning</span></span>

<span data-ttu-id="27af8-102">Pour supprimer une violation de règle, définissez l’option de gravité pour l’ID de règle spécifique sur `none` dans un fichier EditorConfig.</span><span class="sxs-lookup"><span data-stu-id="27af8-102">To suppress a rule violation, set the severity option for the specific rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="27af8-103">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="27af8-103">For example:</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="27af8-104">Visual Studio fournit des méthodes supplémentaires pour supprimer les avertissements des règles d’analyse du code.</span><span class="sxs-lookup"><span data-stu-id="27af8-104">Visual Studio provides additional ways to suppress warnings from code analysis rules.</span></span> <span data-ttu-id="27af8-105">Pour plus d’informations, consultez [Supprimer les violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span><span class="sxs-lookup"><span data-stu-id="27af8-105">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span></span>

<span data-ttu-id="27af8-106">Pour plus d’informations sur les niveaux de gravité de la règle, consultez [configurer la gravité](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)de la règle.</span><span class="sxs-lookup"><span data-stu-id="27af8-106">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>
