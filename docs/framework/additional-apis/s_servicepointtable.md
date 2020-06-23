---
title: ServicePointManager. s_ServicePointTable Field
description: En savoir plus sur le champ ServicePointManager. s_ServicePointTable dans .NET. Ce champ de table de hachage contient des connexions HTTP actives (ServicePoints) dans AppDomain.
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989545"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>Champ ServicePointManager. s \_ ServicePointTable

`ServicePointManager.s_ServicePointTable`est un <xref:System.Collections.Hashtable> qui contient la liste des connexions http actives <xref:System.Net.ServicePoint> dans le <xref:System.AppDomain> .

## <a name="syntax"></a>Syntax
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> Le `ServicePointManager.s_ServicePointTable` champ est privé et n’est pas destiné à être utilisé directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
