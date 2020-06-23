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
# <a name="httpstatusdescription-class"></a>HttpStatusDescription, classe

Fournit des descriptions d’état HTTP standard. Cette classe ne peut pas être héritée.

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.

## <a name="get-method"></a>méthode Get

Retourne la description associée au code d’état HTTP spécifié.

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a>Paramètres

`code` <xref:System.Int32>

Code d’état HTTP, par exemple, `404` .

### <a name="return-value"></a>Valeur retournée

<xref:System.String?displayProperty=nameWithType>

Description de l’état HTTP.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
