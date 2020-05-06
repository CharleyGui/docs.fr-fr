---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936995"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>La police de contrôle par défaut a été remplacée par Segoe UI 9 PT

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, la <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> propriété a la valeur `Microsoft Sans Serif 8 pt`. L’illustration suivante montre une fenêtre qui utilise la police par défaut.

![Police de contrôle par défaut dans .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

À compter de .NET Core 3,0, la police par défaut est `Segoe UI 9 pt` définie sur (la même <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>police que). Suite à cette modification, les formulaires et les contrôles sont dimensionnés à une taille supérieure à 27% pour tenir compte de la taille de la nouvelle police par défaut. Par exemple :

![Police de contrôle par défaut dans .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Cette modification a été apportée pour s’aligner sur [les instructions de l’expérience utilisateur Windows (UX)](/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

En raison de la modification de la taille des formulaires et des contrôles, assurez-vous que votre application s’affiche correctement.

Pour conserver la police d’origine, définissez la police par défaut de `Microsoft Sans Serif 8 pt`votre formulaire sur. Par exemple :

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>Category

- Windows Forms

#### <a name="affected-apis"></a>API affectées

Aucun.

<!--

### Affected APIs

- Not detectable via API analysis

-->
