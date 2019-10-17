---
title: Méthode SqlStreamChars. Flush (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395622"
---
# <a name="sqlstreamcharsflush-method"></a>SqlStreamChars. Flush, méthode

En cas de remplacement dans une classe dérivée, efface toutes les mémoires tampons pour ce flux et provoque l'écriture de toutes les données se trouvant dans des mémoires tampons sur l'appareil sous-jacent. L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll. Elle est destinée à être utilisée par SQL Server. Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.

## <a name="syntax"></a>Syntaxe

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `SqlStreamChars.Flush` est privée et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>spécifications

**Espace de noms :** <xref:System.Data.SqlTypes>

**Assembly :** System. Data (dans System. Data. dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
