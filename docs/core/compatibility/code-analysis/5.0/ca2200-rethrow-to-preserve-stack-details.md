---
title: 'Modification avec rupture : ca2200 : lever à nouveau pour conserver les détails de la pile'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca2200.
ms.date: 09/03/2020
ms.openlocfilehash: 74e169906a8b826328de8d4c5f69c32234c2ce95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761028"
---
# <a name="warning-ca2200-rethrow-to-preserve-stack-details"></a>AVERTISSEMENT ca2200 : lever à nouveau pour conserver les détails de la pile

La règle d’analyseur de code .NET [ca2200](/visualstudio/code-quality/ca2200) est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour tous les `catch` blocs qui lèvent à nouveau une exception et l’exception est explicitement spécifiée dans l' `throw` instruction.

## <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md). Plusieurs de ces règles sont activées par défaut, y compris [ca2200](/visualstudio/code-quality/ca2200). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

Règle ca2200 signale le code où les exceptions sont levées à nouveau et la variable d’exception est spécifiée dans l' `throw` instruction. Lorsqu’une exception est levée, une partie des informations qu’elle transmet est la trace de la pile. La trace de la pile est une liste de la hiérarchie d’appels de méthode qui commence par la méthode qui lève l’exception et se termine par la méthode qui intercepte l’exception. Si une exception est levée à nouveau en spécifiant l’exception dans l' `throw` instruction, la trace de la pile redémarre à la méthode actuelle et la liste des appels de méthode entre la méthode d’origine qui a levé l’exception et la méthode actuelle est perdue. Pour conserver les informations de trace de la pile d’origine avec l’exception, utilisez l' `throw` instruction sans spécifier l’exception.

L’extrait de code suivant ne génère pas d’avertissement pour la règle ca2200. Toutefois, la *ligne commentée déclencherait* une violation.

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

- Lever à nouveau les exceptions sans spécifier explicitement l’exception. Pour plus d’informations, voir [ca2200](/visualstudio/code-quality/ca2200).

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
