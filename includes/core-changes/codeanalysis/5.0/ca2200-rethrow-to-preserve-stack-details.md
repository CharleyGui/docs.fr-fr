---
ms.openlocfilehash: b697bbf6844759de8babd4245667e7b333884ff8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538920"
---
### <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200 : Levez à nouveau une exception pour conserver les détails de la pile

La règle d’analyseur de code .NET [ca2200](/visualstudio/code-quality/ca2200) est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour tous les `catch` blocs qui lèvent à nouveau une exception et l’exception est explicitement spécifiée dans l' `throw` instruction.

#### <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md). Plusieurs de ces règles sont activées par défaut, y compris [ca2200](/visualstudio/code-quality/ca2200). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

Règle ca2200 signale le code où les exceptions sont levées à nouveau et la variable d’exception est spécifiée dans l' `throw` instruction. Lorsqu’une exception est levée, une partie des informations qu’elle transmet est la trace de la pile. La trace de la pile est une liste de la hiérarchie d’appels de méthode qui commence par la méthode qui lève l’exception et se termine par la méthode qui intercepte l’exception. Si une exception est levée à nouveau en spécifiant l’exception dans l' `throw` instruction, la trace de la pile redémarre à la méthode actuelle et la liste des appels de méthode entre la méthode d’origine qui a levé l’exception et la méthode actuelle est perdue. Pour conserver les informations de trace de la pile d’origine avec l’exception, utilisez l' `throw` instruction sans spécifier l’exception.

L’extrait de code suivant ne génère pas d’avertissement pour la règle ca2200. Toutefois, la *ligne commentée déclencherait* une violation.

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

#### <a name="version-introduced"></a>Version introduite

5,0 RC1

#### <a name="recommended-action"></a>Action recommandée

- Lever à nouveau les exceptions sans spécifier explicitement l’exception. Pour plus d’informations, voir [ca2200](/visualstudio/code-quality/ca2200).

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Category

Analyse du code

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
