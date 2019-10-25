---
title: SslState. SslProtocol, propriété (System .net. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 6983ac071dad29b240308031ecd0a3562a6856e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847198"
---
# <a name="sslstatesslprotocol-property"></a>SslState. SslProtocol, propriété

Obtient les versions du protocole SSL.

## <a name="syntax"></a>Syntaxe

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>Valeur de la propriété

<xref:System.Security.Authentication.SslProtocols>  
Combinaison d’opérations de bits des valeurs d’énumération qui spécifient les versions du protocole SSL.

## <a name="remarks"></a>Notes

> [!WARNING]
> La propriété `SslState.SslProtocol` est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>spécifications

**Espace de noms :** <xref:System.Net.Security>

**Assembly :** Système (dans System. dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
