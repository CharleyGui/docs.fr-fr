---
title: Méthode FindHeaderByColumn (System. Windows. Controls. GridViewHeaderRowPresenter)
description: En savoir plus sur la méthode WPF privée appelée FindHeaderByColumn.
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.FindHeaderByColumn
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 88ed2928f86602d1078488354de6d5267c0311f5
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877759"
---
# <a name="findheaderbycolumn-method"></a>Méthode FindHeaderByColumn

Recherche l’en-tête de colonne pour la colonne spécifiée dans l’arborescence d’éléments visuels.

```csharp
private GridViewColumnHeader FindHeaderByColumn(GridViewColumn column)
```

> [!WARNING]
> Cette méthode est privée et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="parameters"></a>Paramètres

`column` <xref:System.Windows.Controls.GridViewColumn>\
Colonne dont l’en-tête doit être trouvé et retourné.

## <a name="return-value"></a>Valeur retournée

<xref:System.Windows.Controls.GridViewColumnHeader>\
En-tête de la colonne spécifiée ou `null` si la colonne spécifiée n’existe pas.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Windows.Controls>

**Assembly :** PresentationFramework.dll

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
