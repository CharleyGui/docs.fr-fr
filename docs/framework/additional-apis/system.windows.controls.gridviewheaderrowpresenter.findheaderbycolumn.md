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
# <a name="findheaderbycolumn-method"></a><span data-ttu-id="c434a-103">Méthode FindHeaderByColumn</span><span class="sxs-lookup"><span data-stu-id="c434a-103">FindHeaderByColumn method</span></span>

<span data-ttu-id="c434a-104">Recherche l’en-tête de colonne pour la colonne spécifiée dans l’arborescence d’éléments visuels.</span><span class="sxs-lookup"><span data-stu-id="c434a-104">Finds the column header for the specified column in the visual tree.</span></span>

```csharp
private GridViewColumnHeader FindHeaderByColumn(GridViewColumn column)
```

> [!WARNING]
> <span data-ttu-id="c434a-105">Cette méthode est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c434a-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c434a-106">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="c434a-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="c434a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c434a-107">Parameters</span></span>

<span data-ttu-id="c434a-108">`column` <xref:System.Windows.Controls.GridViewColumn></span><span class="sxs-lookup"><span data-stu-id="c434a-108">`column` <xref:System.Windows.Controls.GridViewColumn></span></span>\
<span data-ttu-id="c434a-109">Colonne dont l’en-tête doit être trouvé et retourné.</span><span class="sxs-lookup"><span data-stu-id="c434a-109">The column whose header should be found and returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="c434a-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c434a-110">Return value</span></span>

<xref:System.Windows.Controls.GridViewColumnHeader>\
<span data-ttu-id="c434a-111">En-tête de la colonne spécifiée ou `null` si la colonne spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="c434a-111">The header of the specified column, or `null` if the specified column doesn't exist.</span></span>

## <a name="requirements"></a><span data-ttu-id="c434a-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c434a-112">Requirements</span></span>

<span data-ttu-id="c434a-113">**Espace de noms :** <xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="c434a-113">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="c434a-114">**Assembly :** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="c434a-114">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="c434a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c434a-115">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
