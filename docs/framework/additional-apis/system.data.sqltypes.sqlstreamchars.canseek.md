---
title: Propriété SqlStreamChars. CanSeek (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395777"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars. CanSeek, propriété

En cas de substitution dans une classe dérivée, obtient une valeur qui indique si le flux en cours prend en charge l’opération de recherche. L’assembly qui contient cette propriété a une relation Friend avec SQLAccess. dll. Elle est destinée à être utilisée par SQL Server. Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Valeur de la propriété

<xref:System.Boolean>\
`true` si le flux actuel prend en charge l’opération de recherche ; dans le cas contraire, `false`.

## <a name="remarks"></a>Notes

> [!WARNING]
> La propriété `SqlStreamChars.CanSeek` est privée et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>spécifications

**Espace de noms :** <xref:System.Data.SqlTypes>

**Assembly :** System. Data (dans System. Data. dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
