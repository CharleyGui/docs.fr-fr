---
title: Méthode SqlStreamChars. Read (Char [], Int32, Int32) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395752"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>Méthode SqlStreamChars. Read (Char [], Int32, Int32)

En cas de substitution dans une classe dérivée, lit le jeu de caractères suivant dans le flux d’entrée. L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll. Elle est destinée à être utilisée par SQL Server. Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Paramètres

`buffer`\
Tableau de caractères à lire.

`offset`\
Décalage par rapport à Origin.

`count`\
Nombre de caractères à lire à partir du flux actuel.

## <a name="returns"></a>Returns (Retours)

<xref:System.Int32>\
Nombre total de caractères lus dans la mémoire tampon.

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `SqlStreamChars.Read` est privée et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>spécifications

**Espace de noms :** <xref:System.Data.SqlTypes>

**Assembly :** System. Data (dans System. Data. dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
