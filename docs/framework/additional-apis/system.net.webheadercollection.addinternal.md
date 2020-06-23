---
title: Méthode WebHeaderCollection. AddInternal (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990323"
---
# <a name="webheadercollectionaddinternal-method"></a>Méthode WebHeaderCollection. AddInternal

Ajoute un nouvel en-tête avec le nom et la valeur spécifiés à la collection, en ignorant les vérifications.

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> Cette méthode est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="parameters"></a>Paramètres

- `name` <xref:System.String>

  Nom de l'en-tête.

- `value` <xref:System.String>

  Valeur de l'en-tête.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
