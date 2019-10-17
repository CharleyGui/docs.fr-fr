---
title: Exception. PrepForRemoting, méthode (System)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405031"
---
# <a name="exceptionprepforremoting-method"></a>Exception. PrepForRemoting, méthode

Conserve la trace de la pile côté serveur en l’ajoutant au message avant que l’exception ne soit levée à nouveau sur le site d’appel client.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Returns (Retours)

<xref:System.Exception>  
Cette instance de l'objet <xref:System.Exception>.

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `Exception.PrepForRemoting` est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>spécifications

**Espace de noms :** <xref:System>

**Assembly :** mscorlib. dll (dans mscorlib. dll)

**Versions de .NET Framework :** Disponible depuis 1,0.
