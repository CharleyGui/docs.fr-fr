---
ms.openlocfilehash: 54bee14f6de409550357194e905b6ee5d8ef8f18
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678995"
---
### <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>OutputType défini sur WinExe pour les applications WPF et WinForms

`OutputType` a automatiquement la valeur `WinExe` pour les applications Windows Presentation Foundation (WPF) et Windows Forms. Lorsque `OutputType` a la valeur `WinExe` , une fenêtre de console ne s’ouvre pas lorsque l’application est exécutée.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, la valeur spécifiée pour `OutputType` dans le fichier projet est utilisée. Exemple :

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

À compter de .NET 5,0, `OutputType` a automatiquement la valeur `WinExe` pour WPF et les applications Windows Forms. Exemple :

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

#### <a name="reason-for-change"></a>Motif de modification

Il est supposé que la plupart des utilisateurs ne souhaitent pas qu’une fenêtre de console s’ouvre quand une application WPF ou Windows Forms est exécutée. En outre, à [présent que ces types d’applications utilisent le kit de développement logiciel (SDK) .net](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) au lieu du Windows Desktop SDK, la valeur par défaut correcte est définie. De plus, lorsque la prise en charge du ciblage d’iOS et d’Android est ajoutée, il sera plus facile de cibler plusieurs plateformes entre plusieurs plateformes si elles utilisent toutes le même type de sortie.

#### <a name="version-introduced"></a>Version introduite

.NET 5,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de votre part. Toutefois, si vous souhaitez revenir à l’ancien comportement, affectez à la `DisableWinExeOutputInference` propriété la valeur `true` dans votre fichier projet.

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

#### <a name="category"></a>Category

- Windows Forms
- Windows Presentation Framework (WPF)

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
