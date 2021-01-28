---
ms.openlocfilehash: b26e346f7076a57aef8ae7587ab1222b4100a323
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957934"
---
## <a name="suppress-a-warning"></a>Supprimer un avertissement

Pour supprimer une violation de règle, définissez l’option de gravité pour l’ID de règle spécifique sur `none` dans un fichier EditorConfig. Par exemple :

```ini
[*.{cs,vb}]
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio fournit des méthodes supplémentaires pour supprimer les avertissements des règles d’analyse du code. Pour plus d’informations, consultez [Supprimer les violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).

Pour plus d’informations sur les niveaux de gravité de la règle, consultez [configurer la gravité](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)de la règle.
