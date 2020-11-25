---
title: 'Modification avec rupture : le ActivityIdFormat par défaut est W3C'
description: En savoir plus sur le changement critique .NET 5,0 dans les bibliothèques .NET de base où le ActivityIdFormat par défaut est désormais W3C.
ms.date: 11/01/2020
ms.openlocfilehash: 77ee705ac18065c84ddeab3127e01b6a40c3b84d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761070"
---
# <a name="default-activityidformat-is-w3c"></a>Le ActivityIdFormat par défaut est W3C

Le format d’identificateur par défaut pour Activity ( <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> ) est Now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .

## <a name="change-description"></a>Description de la modification

Le format de l’ID d’activité W3C a été introduit dans .NET Core 3,0 comme alternative au format d’ID hiérarchique. Toutefois, pour préserver la compatibilité, le format W3C n’a pas effectué la valeur par défaut tant que .NET 5,0. La valeur par défaut a été modifiée dans .NET 5,0, car le [format W3C a été ratifié et a](https://www.w3.org/TR/trace-context/) obtenu une traction sur plusieurs implémentations de langage.

Si votre application cible une plateforme autre que .NET 5,0 ou une version ultérieure, elle rencontre l’ancien comportement, où <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> est le format par défaut. Cette valeur par défaut s’applique aux plateformes Net45 +, netstandard 1.1 + et netcoreapp (1. x, 2. x et 3. x). Dans .NET 5,0 et versions ultérieures, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> a la valeur <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Si votre application est indépendante de l’identificateur utilisé pour le traçage distribué, aucune action n’est nécessaire. Des bibliothèques telles que ASP.NET Core et <xref:System.Net.Http.HttpClient> peuvent utiliser ou propager les deux versions du <xref:System.Diagnostics.ActivityIdFormat> .

Si vous avez besoin d’une interopérabilité avec les systèmes existants ou si les systèmes actuels s’appuient sur le format de l’identificateur, vous pouvez conserver l’ancien comportement en affectant à la valeur <xref:System.Diagnostics.Activity.DefaultIdFormat> <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> . Vous pouvez également définir un commutateur AppContext de l’une des trois façons suivantes :

- Dans le fichier projet.

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- Dans le fichier *runtimeconfig.js* .

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- Via une variable d’environnement.

  Défini `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` sur `true` ou 1.

## <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
