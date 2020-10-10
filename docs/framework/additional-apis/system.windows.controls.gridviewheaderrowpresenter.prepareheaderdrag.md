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
# <a name="prepareheaderdrag-method"></a><span data-ttu-id="f278d-103">Méthode PrepareHeaderDrag</span><span class="sxs-lookup"><span data-stu-id="f278d-103">PrepareHeaderDrag method</span></span>

<span data-ttu-id="f278d-104">Prépare l’en-tête de colonne spécifié pour la réorganisation.</span><span class="sxs-lookup"><span data-stu-id="f278d-104">Prepares the specified column header for reordering.</span></span>

```csharp
private void PrepareHeaderDrag(GridViewColumnHeader header, Point pos, Point relativePos, bool cancelInvoke)
```

> [!WARNING]
> <span data-ttu-id="f278d-105">Cette méthode est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f278d-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f278d-106">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="f278d-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="f278d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f278d-107">Parameters</span></span>

<span data-ttu-id="f278d-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span><span class="sxs-lookup"><span data-stu-id="f278d-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span></span>\
<span data-ttu-id="f278d-109">En-tête de colonne à préparer pour la réorganisation.</span><span class="sxs-lookup"><span data-stu-id="f278d-109">The column header to prepare for reordering.</span></span>

<span data-ttu-id="f278d-110">`pos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="f278d-110">`pos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="f278d-111">Position, par rapport à <xref:System.Windows.Controls.GridViewHeaderRowPresenter> , à laquelle le glissement commence.</span><span class="sxs-lookup"><span data-stu-id="f278d-111">The position, relative to <xref:System.Windows.Controls.GridViewHeaderRowPresenter>, where the dragging starts.</span></span>

<span data-ttu-id="f278d-112">`relativePos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="f278d-112">`relativePos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="f278d-113">Position, par rapport à `header` , à laquelle le glissement commence.</span><span class="sxs-lookup"><span data-stu-id="f278d-113">The position, relative to `header`, where the dragging starts.</span></span>

<span data-ttu-id="f278d-114">`cancelInvoke` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="f278d-114">`cancelInvoke` <xref:System.Boolean></span></span>\
<span data-ttu-id="f278d-115">`true` pour annuler la réorganisation ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="f278d-115">`true` to cancel the reordering; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="f278d-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f278d-116">Requirements</span></span>

<span data-ttu-id="f278d-117">**Espace de noms :** <xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="f278d-117">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="f278d-118">**Assembly :** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="f278d-118">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="f278d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f278d-119">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
