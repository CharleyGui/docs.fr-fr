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
# <a name="pooledstreamnetworkstream-property"></a>PooledStream. NetworkStream, propriété

Obtient ou définit le flux réseau pour le socket `PooledStream`.

## <a name="syntax"></a>Syntaxe

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>Valeur de la propriété

<xref:System.Net.Sockets.NetworkStream>  
Flux réseau pour le socket de `PooledStream`.

## <a name="remarks"></a>Notes

> [!WARNING]
> La propriété `PooledStream.NetworkStream` est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (dans System. dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
