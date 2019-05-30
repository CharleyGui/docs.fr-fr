---
title: Champ de ConnectionGroup.m_ConnectionList
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d06968c844dc9187b973af156a29ded9ba7cde66
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301406"
---
# <a name="connectiongroupmconnectionlist-field"></a>ConnectionGroup.m\_ConnectionList champ

`ConnectionGroup.m_ConnectionList` est un <xref:System.Collections.ArrayList> des objets de connexion qui sert le même URI et le partage les mêmes valeurs pour d’autres propriétés comme expiration et l’authentification.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> Le `ConnectionGroup.m_ConnectionList` champ est privé et n’est pas destiné à être utilisé directement dans votre code.
> 
> Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.

## <a name="requirements"></a>Configuration requise

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (dans System.dll)

**Versions du .NET framework :** Disponible à partir de 2.0.
