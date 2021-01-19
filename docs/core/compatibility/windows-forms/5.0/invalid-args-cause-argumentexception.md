---
title: 'Modification avec rupture : les méthodes WinForms lèvent désormais ArgumentException'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où certaines méthodes Windows Forms lèvent désormais une exception ArgumentException pour les arguments non valides.
ms.date: 07/18/2020
ms.openlocfilehash: 892f4d16b80f3e42187480a7fcfb24e81868d07c
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570214"
---
# <a name="winforms-methods-now-throw-argumentexception"></a>Les méthodes WinForms lèvent désormais ArgumentException

Certaines méthodes Windows Forms lèvent désormais un <xref:System.ArgumentException> pour les arguments non valides, dans le cas contraire.

## <a name="change-description"></a>Description de la modification

Auparavant, passer des arguments d’un type inattendu ou incorrect à certaines méthodes Windows Forms entraînerait un état indéterminé. À compter de .NET 5,0, ces méthodes lèvent désormais une exception <xref:System.ArgumentException> en cas de transmission d’arguments non valides.

La levée d’une <xref:System.ArgumentException> conforme au comportement du Runtime .net. Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.

## <a name="version-introduced"></a>Version introduite

.NET 5.0

## <a name="recommended-action"></a>Action recommandée

- Mettez à jour le code pour empêcher le passage d’arguments non valides.
- Si nécessaire, gérez un <xref:System.ArgumentException> lors de l’appel de la méthode.

## <a name="affected-apis"></a>API affectées

Le tableau suivant répertorie les méthodes et les paramètres affectés :

| Méthode | Nom du paramètre | Condition | Version ajoutée |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | L’argument n’est pas de type <xref:System.Windows.Forms.TabPage> . | Preview 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | L’argument est `null` , <xref:System.String.Empty?displayProperty=nameWithType> , ou un espace blanc. | Préversion 5 |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | Impossible de récupérer un `InputLanguage` pour la culture spécifiée. | Version préliminaire 7 |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
