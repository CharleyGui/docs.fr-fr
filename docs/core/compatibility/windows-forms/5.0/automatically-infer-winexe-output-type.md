---
title: 'Modification avec rupture : OutputType défini sur WinExe pour les applications WPF et WinForms'
description: En savoir plus sur la modification avec rupture dans le kit de développement logiciel (SDK) .NET 5.0.100 où OutputType est automatiquement défini sur WinExe pour les applications Windows Forms.
ms.date: 09/18/2020
ms.openlocfilehash: 0b56db57d5242f2fb001c4de339a7f696c088dfc
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633853"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>OutputType défini sur WinExe pour les applications WPF et WinForms

`OutputType` a automatiquement la valeur `WinExe` pour les applications Windows Presentation Foundation (WPF) et Windows Forms. Lorsque `OutputType` a la valeur `WinExe` , une fenêtre de console ne s’ouvre pas lorsque l’application est exécutée.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes du kit de développement logiciel (SDK) .NET, la valeur spécifiée pour `OutputType` dans le fichier projet est utilisée. Par exemple :

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

À partir de la version 5.0.100 du kit de développement logiciel (SDK) .NET, `OutputType` a automatiquement la valeur `WinExe` pour WPF et les applications Windows Forms qui ciblent toute version du Framework, y compris .NET Framework. Par exemple :

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a>Motif de modification

Il est supposé que la plupart des utilisateurs ne souhaitent pas qu’une fenêtre de console s’ouvre quand une application WPF ou Windows Forms est exécutée. En outre, à [présent que ces types d’applications utilisent le kit de développement logiciel (SDK) .net](sdk-and-target-framework-change.md) au lieu du Windows Desktop SDK, la valeur par défaut correcte est définie. De plus, lorsque la prise en charge du ciblage d’iOS et d’Android est ajoutée, il sera plus facile de cibler plusieurs plateformes entre plusieurs plateformes si elles utilisent toutes le même type de sortie.

## <a name="version-introduced"></a>Version introduite

5.0.100 .NET

## <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de votre part. Toutefois, si vous souhaitez revenir à l’ancien comportement, affectez à la `DisableWinExeOutputInference` propriété la valeur `true` dans votre fichier projet.

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
