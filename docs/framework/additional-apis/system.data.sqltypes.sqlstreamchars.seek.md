---
title: Méthode SqlStreamChars.Seek (Int64, SeekOrigin) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 6b69f87da9fb3829d765dc135de1f6c10765b63a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634360"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="b619e-102">Méthode de SqlStreamChars.Seek (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="b619e-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="b619e-103">En cas de remplacement dans une classe dérivée, définit la position dans le flux actuel.</span><span class="sxs-lookup"><span data-stu-id="b619e-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="b619e-104">L’assembly qui contient cette méthode a une relation de friend avec SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="b619e-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="b619e-105">Il est prévu pour une utilisation par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b619e-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="b619e-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="b619e-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="b619e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b619e-107">Parameters</span></span>

`offset`\
<span data-ttu-id="b619e-108">Offset d’octet par rapport à `origin`.</span><span class="sxs-lookup"><span data-stu-id="b619e-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="b619e-109">Une des valeurs d’énumération qui indique le point de référence à partir de laquelle obtenir la nouvelle position.</span><span class="sxs-lookup"><span data-stu-id="b619e-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="b619e-110">Returns (Retours)</span><span class="sxs-lookup"><span data-stu-id="b619e-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="b619e-111">Nouvelle position dans le flux actuel.</span><span class="sxs-lookup"><span data-stu-id="b619e-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="b619e-112">Notes</span><span class="sxs-lookup"><span data-stu-id="b619e-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b619e-113">Le `SqlStreamChars.Seek` méthode est privée et qu’il n’est pas destiné à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="b619e-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b619e-114">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="b619e-114">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b619e-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b619e-115">Requirements</span></span>

<span data-ttu-id="b619e-116">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="b619e-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="b619e-117">**Assembly :** System.Data (dans System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="b619e-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="b619e-118">**Versions du .NET framework :** Disponible à partir de 2.0.</span><span class="sxs-lookup"><span data-stu-id="b619e-118">**.NET Framework versions:** Available since 2.0.</span></span>
