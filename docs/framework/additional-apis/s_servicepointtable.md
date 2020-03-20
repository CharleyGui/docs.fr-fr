---
title: ServicePointManager.s_ServicePointTable Champ
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
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155810"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>ServicePointManager.s\_ServicePointTable Field (en anglais)

`ServicePointManager.s_ServicePointTable`est <xref:System.Collections.Hashtable> un qui contient la liste<xref:System.Net.ServicePoint>des connexions HTTP actives (s) dans le <xref:System.AppDomain>.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> Le `ServicePointManager.s_ServicePointTable` champ est privé et n’est pas destiné à être utilisé directement dans votre code.
>
> Microsoft ne prend en charge l’utilisation de ce champ dans une application de production en aucune circonstance.

## <a name="requirements"></a>Spécifications

**Espace nom:**<xref:System.Net>

**Assemblée:** Système (dans System.dll)

**.NET Versions du Cadre:** Disponible depuis 2.0.
