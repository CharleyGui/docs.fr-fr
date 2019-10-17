---
title: Propriété SqlStreamChars. length (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395609"
---
# <a name="sqlstreamcharslength-property"></a>SqlStreamChars. Length, propriété

En cas de substitution dans une classe dérivée, obtient la longueur du flux actuel. L’assembly qui contient cette propriété a une relation Friend avec SQLAccess. dll. Elle est destinée à être utilisée par SQL Server. Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.

## <a name="syntax"></a>Syntaxe

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a>Valeur de la propriété

<xref:System.Int64>\
Longueur du flux.

## <a name="remarks"></a>Notes

> [!WARNING]
> La propriété `SqlStreamChars.Length` est privée et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>spécifications

**Espace de noms :** <xref:System.Data.SqlTypes>

**Assembly :** System. Data (dans System. Data. dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
