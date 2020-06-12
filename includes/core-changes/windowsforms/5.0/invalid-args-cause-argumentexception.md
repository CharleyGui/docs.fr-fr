---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702435"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Les méthodes WinForms lèvent désormais ArgumentException

Certaines méthodes Windows Forms lèvent désormais un <xref:System.ArgumentException> pour les arguments non valides, dans le cas contraire.

#### <a name="change-description"></a>Description de la modification

Auparavant, passer des arguments d’un type inattendu ou incorrect à certaines méthodes Windows Forms entraînerait un état indéterminé. À compter de .NET 5,0, ces méthodes lèvent désormais une exception <xref:System.ArgumentException> en cas de transmission d’arguments non valides.

La levée d’une <xref:System.ArgumentException> conforme au comportement du Runtime .net. Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.

Le tableau suivant répertorie les méthodes et les paramètres affectés :

| Méthode | Nom du paramètre | Condition | Version ajoutée |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | L’argument n’est pas de type <xref:System.Windows.Forms.TabPage> . | 5,0 Preview 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | L’argument est `null` , <xref:System.String.Empty?displayProperty=nameWithType> , ou un espace blanc. | 5,0 Preview 5 |

#### <a name="version-introduced"></a>Version introduite

.NET 5,0

#### <a name="recommended-action"></a>Action recommandée

- Mettez à jour le code pour empêcher le passage d’arguments non valides.
- Si nécessaire, gérez un <xref:System.ArgumentException> lors de l’appel de la méthode.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
