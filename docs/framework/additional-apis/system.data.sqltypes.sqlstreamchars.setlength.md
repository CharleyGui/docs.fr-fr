---
title: Méthode SqlStreamChars. SetLength (Int64) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 291d6e9395581f2370dafc728521a314d54a686d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395723"
---
# <a name="sqlstreamcharssetlengthint64-method"></a>Méthode SqlStreamChars. SetLength (Int64)

En cas de substitution dans une classe dérivée, libère les ressources utilisées par le flux. L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll. Elle est destinée à être utilisée par SQL Server. Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a>Paramètres

`value`\
Longueur souhaitée du flux actuel en octets.

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `SqlStreamChars.SetLength` est privée et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>spécifications

**Espace de noms :** <xref:System.Data.SqlTypes>

**Assembly :** System. Data (dans System. Data. dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
