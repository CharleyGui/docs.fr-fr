---
title: HttpStatusDescription, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990392"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="7ff8a-102">HttpStatusDescription, classe</span><span class="sxs-lookup"><span data-stu-id="7ff8a-102">HttpStatusDescription class</span></span>

<span data-ttu-id="7ff8a-103">Fournit des descriptions d’état HTTP standard.</span><span class="sxs-lookup"><span data-stu-id="7ff8a-103">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="7ff8a-104">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="7ff8a-104">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="7ff8a-105">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="7ff8a-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7ff8a-106">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="7ff8a-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="7ff8a-107">méthode Get</span><span class="sxs-lookup"><span data-stu-id="7ff8a-107">Get method</span></span>

<span data-ttu-id="7ff8a-108">Retourne la description associée au code d’état HTTP spécifié.</span><span class="sxs-lookup"><span data-stu-id="7ff8a-108">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="7ff8a-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ff8a-109">Parameters</span></span>

<span data-ttu-id="7ff8a-110">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="7ff8a-110">`code` <xref:System.Int32></span></span>

<span data-ttu-id="7ff8a-111">Code d’état HTTP, par exemple, `404` .</span><span class="sxs-lookup"><span data-stu-id="7ff8a-111">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="7ff8a-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7ff8a-112">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="7ff8a-113">Description de l’état HTTP.</span><span class="sxs-lookup"><span data-stu-id="7ff8a-113">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="7ff8a-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7ff8a-114">Requirements</span></span>

<span data-ttu-id="7ff8a-115">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="7ff8a-115">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="7ff8a-116">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="7ff8a-116">**Assembly:** System (in System.dll)</span></span>
