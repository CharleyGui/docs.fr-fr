---
title: Constructeur SqlStreamChars (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars..ctor
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7de715d2833f4aa26f8251e32e6bf8853b0bd704
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634596"
---
# <a name="sqlstreamchars-constructor"></a>SqlStreamChars, constructeur

Initialise une nouvelle instance de la classe `SqlStreamChars`. L’assembly qui contient ce constructeur a une relation de friend avec SQLAccess.dll. Il est prévu pour une utilisation par SQL Server. Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.

```csharp
protected SqlStreamChars ();
```

## <a name="remarks"></a>Notes

> [!WARNING]
> Le `SqlStreamChars` constructeur est protégé et n’est pas destiné à être utilisé directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.

## <a name="requirements"></a>Configuration requise

**Espace de noms :** <xref:System.Data.SqlTypes>

**Assembly :** System.Data (dans System.Data.dll)

**Versions du .NET framework :** Disponible à partir de 2.0.
