---
title: Méthode WebHeaderCollection. AddInternal (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990323"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="4e03f-102">Méthode WebHeaderCollection. AddInternal</span><span class="sxs-lookup"><span data-stu-id="4e03f-102">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="4e03f-103">Ajoute un nouvel en-tête avec le nom et la valeur spécifiés à la collection, en ignorant les vérifications.</span><span class="sxs-lookup"><span data-stu-id="4e03f-103">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="4e03f-104">Cette méthode est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="4e03f-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4e03f-105">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="4e03f-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="4e03f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e03f-106">Parameters</span></span>

- <span data-ttu-id="4e03f-107">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="4e03f-107">`name` <xref:System.String></span></span>

  <span data-ttu-id="4e03f-108">Nom de l'en-tête.</span><span class="sxs-lookup"><span data-stu-id="4e03f-108">The name of the header.</span></span>

- <span data-ttu-id="4e03f-109">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="4e03f-109">`value` <xref:System.String></span></span>

  <span data-ttu-id="4e03f-110">Valeur de l'en-tête.</span><span class="sxs-lookup"><span data-stu-id="4e03f-110">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="4e03f-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4e03f-111">Requirements</span></span>

<span data-ttu-id="4e03f-112">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="4e03f-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="4e03f-113">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="4e03f-113">**Assembly:** System (in System.dll)</span></span>
