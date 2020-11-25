---
title: 'Modification avec rupture : ca1417 : OutAttribute sur le paramètre de chaîne pour P/Invoke'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca1417.
ms.date: 09/29/2020
ms.openlocfilehash: 3316d07108ec7f9da985494413336cba6d560dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760824"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a>AVERTISSEMENT ca1417 : OutAttribute sur le paramètre de chaîne pour P/Invoke

La [règle de](/visualstudio/code-quality/ca1417) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour toutes les définitions de méthode d’appel de code non [managé (P/Invoke)](../../../../standard/native-interop/pinvoke.md) quand un <xref:System.String> paramètre est passé par valeur et marqué avec <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md). Plusieurs de ces règles sont activées par défaut, y compris [ca1417](/visualstudio/code-quality/ca1417). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

La règle ca1417 marque les définitions de méthode [P/Invoke](../../../../standard/native-interop/pinvoke.md) quand un <xref:System.String> paramètre est marqué avec l' <xref:System.Runtime.InteropServices.OutAttribute> attribut et est passé par valeur. Par exemple :

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

Le Runtime .NET gère une table, appelée pool interne, qui contient une référence unique à chaque chaîne littérale unique dans un programme. Si une chaîne internée marquée avec <xref:System.Runtime.InteropServices.OutAttribute> est passée par valeur à une méthode P/Invoke, le runtime peut être déstabilisé. Pour plus d’informations sur l’internement des chaînes, consultez les notes relatives à <xref:System.String.Intern(System.String)?displayProperty=nameWithType> .

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

- Si vous devez marshaler à nouveau les données de chaîne modifiées vers l’appelant, transmettez la chaîne par référence à la place.

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- Si vous n’avez pas besoin de marshaler à nouveau les données de chaîne modifiées vers l’appelant, supprimez simplement <xref:System.Runtime.InteropServices.OutAttribute> .

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  Pour plus d’informations, consultez [ca1417](/visualstudio/code-quality/ca1417).

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
