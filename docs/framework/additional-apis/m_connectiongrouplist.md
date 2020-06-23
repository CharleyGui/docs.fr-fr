---
title: ServicePoint. m_ConnectionGroupList Field
description: Comprendre le champ ServicePoint. m_ConnectionGroupList, une table de hachage des groupes de connexions qui contiennent chacun une connexion pour l’URI ServicePoint dans .NET.
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: 0ebfeb782147f21abfde536b8053fa15b1e1a602
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989707"
---
# <a name="servicepointm_connectiongrouplist-field"></a>Champ ServicePoint. m \_ ConnectionGroupList

`ServicePoint.m_ConnectionGroupList`est un <xref:System.Collections.Hashtable> des groupes de connexions, chacun contenant une connexion pour l' <xref:System.Net.ServicePoint> URI de.

## <a name="syntax"></a>Syntax
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> Le `ServicePoint.m_ConnectionGroupList` champ est privé et n’est pas destiné à être utilisé directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
