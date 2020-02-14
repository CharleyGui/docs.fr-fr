---
title: Exception. PrepForRemoting, méthode (System)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214899"
---
# <a name="exceptionprepforremoting-method"></a>Exception.PrepForRemoting, méthode

Conserve la trace de la pile côté serveur en l’ajoutant au message avant que l’exception ne soit levée à nouveau sur le site d’appel client.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Retours

<xref:System.Exception>  
Cette instance de l'objet <xref:System.Exception>.

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `Exception.PrepForRemoting` est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System>

**Assembly :** mscorlib. dll (dans mscorlib. dll)

**Versions de .NET Framework :** Disponible depuis 1,0.
