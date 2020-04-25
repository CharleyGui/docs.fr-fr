---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158392"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Les méthodes WinForms lèvent désormais ArgumentException

Certaines méthodes Windows Forms lèvent désormais <xref:System.ArgumentException> un pour les arguments non valides, dans le cas contraire.

#### <a name="change-description"></a>Description de la modification

Auparavant, passer des arguments d’un type inattendu ou incorrect à certaines méthodes Windows Forms entraînerait un état indéterminé. À compter de .NET 5,0, ces méthodes lèvent <xref:System.ArgumentException> désormais une exception en cas de transmission d’arguments non valides.

La levée <xref:System.ArgumentException> d’une conforme au comportement du Runtime .net. Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.

Le tableau suivant répertorie les méthodes et les paramètres affectés :

| Méthode | Nom du paramètre | Condition | Version ajoutée |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | L’argument n’est pas <xref:System.Windows.Forms.TabPage>de type. | 5,0 Preview 1 |

#### <a name="version-introduced"></a>Version introduite

.NET 5,0 Preview 1

#### <a name="recommended-action"></a>Action recommandée

- Mettez à jour le code pour empêcher le passage d’arguments non valides.
- Si nécessaire, gérez un <xref:System.ArgumentException> lors de l’appel de la méthode.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
