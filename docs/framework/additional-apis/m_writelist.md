---
title: Champ de Connection.m_WriteList
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d138e0490e849ff26f540077ec7d23ae42737606
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300909"
---
# <a name="connectionmwritelist-field"></a>Connection.m\_WriteList champ

`Connection.m_WriteList` est un <xref:System.Collections.ArrayList> de <xref:System.Net.HttpWebRequest> les objets qui sont la file d’attente d’être envoyés via HTTP.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> Le `Connection.m_WriteList` champ est privé et n’est pas destiné à être utilisé directement dans votre code.
> 
> Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.

## <a name="requirements"></a>Configuration requise

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (dans System.dll)

**Versions du .NET framework :** Disponible à partir de 2.0.
