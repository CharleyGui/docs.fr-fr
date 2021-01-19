---
title: 'Modification avec rupture : certaines propriétés TableLayoutSettings lèvent InvalidEnumArgumentException'
description: Découvrez la modification avec rupture dans .NET 6,0 où certaines API TableLayoutSettings lèvent désormais une InvalidEnumArgumentException pour les arguments non valides.
ms.date: 01/18/2021
ms.openlocfilehash: 8397952e4647347718f11597a100c5d764e7186b
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570268"
---
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a>Les propriétés TableLayoutSettings sélectionnées lèvent InvalidEnumArgumentException

Les <xref:System.Windows.Forms.TableLayoutSettings> propriétés sélectionnées lèvent désormais une exception <xref:System.ComponentModel.InvalidEnumArgumentException> si vous tentez d’assigner une valeur incorrecte.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, ces propriétés lèvent une exception <xref:System.ArgumentOutOfRangeException> si vous tentez d’assigner une valeur incorrecte. À compter de .NET 6,0, ces propriétés lèvent un <xref:System.ComponentModel.InvalidEnumArgumentException> dans de tels cas.

## <a name="reason-for-change"></a>Motif de modification

<xref:System.ComponentModel.InvalidEnumArgumentException>La levée est conforme à l’API Windows Forms existante dans des situations similaires. La levée de cette exception offre également aux développeurs une meilleure expérience de débogage.

## <a name="version-introduced"></a>Version introduite

.NET 6,0

## <a name="recommended-action"></a>Action recommandée

- Mettez à jour le code pour empêcher d’assigner des valeurs incorrectes.
- Si nécessaire, gérez une <xref:System.ComponentModel.InvalidEnumArgumentException> lors de l’accès à ces API.

## <a name="affected-apis"></a>API affectées

Le tableau suivant répertorie les propriétés affectées :

| Propriété | Version modifiée |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | Preview 1 |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | Preview 1 |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
