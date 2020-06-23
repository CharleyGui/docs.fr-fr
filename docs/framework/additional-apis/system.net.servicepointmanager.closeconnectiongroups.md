---
title: ServicePointManager. CloseConnectionGroups, méthode (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990366"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a>ServicePointManager. CloseConnectionGroups, méthode

Itère au sein de tous les points de service et ferme les groupes de connexions portant le nom spécifié.

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> Cette méthode est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="parameters"></a>Paramètres

`connectionGroupName` <xref:System.String>

Nom du groupe de connexions à fermer.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
