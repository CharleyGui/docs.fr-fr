---
title: Méthode PrepareHeaderDrag (System. Windows. Controls. GridViewHeaderRowPresenter)
description: En savoir plus sur la méthode WPF privée appelée PrepareHeaderDrag.
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.PrepareHeaderDrag
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 6d806b8a50de3234cd04198f4ab86621dcd6ede1
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877750"
---
# <a name="prepareheaderdrag-method"></a>Méthode PrepareHeaderDrag

Prépare l’en-tête de colonne spécifié pour la réorganisation.

```csharp
private void PrepareHeaderDrag(GridViewColumnHeader header, Point pos, Point relativePos, bool cancelInvoke)
```

> [!WARNING]
> Cette méthode est privée et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="parameters"></a>Paramètres

`header` <xref:System.Windows.Controls.GridViewColumnHeader>\
En-tête de colonne à préparer pour la réorganisation.

`pos` <xref:System.Windows.Point>\
Position, par rapport à <xref:System.Windows.Controls.GridViewHeaderRowPresenter> , à laquelle le glissement commence.

`relativePos` <xref:System.Windows.Point>\
Position, par rapport à `header` , à laquelle le glissement commence.

`cancelInvoke` <xref:System.Boolean>\
`true` pour annuler la réorganisation ; Sinon, `false` .

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Windows.Controls>

**Assembly :** PresentationFramework.dll

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
