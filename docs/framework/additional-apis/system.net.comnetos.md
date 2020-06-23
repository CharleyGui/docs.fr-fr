---
title: ComNetOS, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990401"
---
# <a name="comnetos-class"></a>ComNetOS, classe

Fournit des informations sur le système d’exploitation actuel, telles que sa version et son type d’installation (client ou serveur). Cette classe ne peut pas être héritée.
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.

## <a name="iswin7orlater-field"></a>Champ IsWin7orLater

Spécifie si la version du système d’exploitation est Windows 7 ou version ultérieure.

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
