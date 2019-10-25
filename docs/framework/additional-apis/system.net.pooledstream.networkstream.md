---
title: PooledStream. NetworkStream, propriété (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 541b8c94b30675c1286b48a2291c3bd3e4aeea0b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847177"
---
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="3346c-102">PooledStream. NetworkStream, propriété</span><span class="sxs-lookup"><span data-stu-id="3346c-102">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="3346c-103">Obtient ou définit le flux réseau pour le socket `PooledStream`.</span><span class="sxs-lookup"><span data-stu-id="3346c-103">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="3346c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3346c-104">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="3346c-105">Valeur de la propriété</span><span class="sxs-lookup"><span data-stu-id="3346c-105">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="3346c-106">Flux réseau pour le socket de `PooledStream`.</span><span class="sxs-lookup"><span data-stu-id="3346c-106">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="3346c-107">Notes</span><span class="sxs-lookup"><span data-stu-id="3346c-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="3346c-108">La propriété `PooledStream.NetworkStream` est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="3346c-108">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="3346c-109">Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="3346c-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="3346c-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="3346c-110">Requirements</span></span>

<span data-ttu-id="3346c-111">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="3346c-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="3346c-112">**Assembly :** Système (dans System. dll)</span><span class="sxs-lookup"><span data-stu-id="3346c-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="3346c-113">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="3346c-113">**.NET Framework versions:** Available since 2.0.</span></span>
