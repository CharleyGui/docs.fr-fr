---
title: Exception. PrepForRemoting, méthode (System)
description: Passez en revue la méthode exception. PrepForRemoting dans .NET. La méthode ajoute la trace de la pile côté serveur au message avant que l’exception ne soit levée à nouveau sur le client.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105261"
---
# <a name="exceptionprepforremoting-method"></a>Exception.PrepForRemoting, méthode

Conserve la trace de la pile côté serveur en l’ajoutant au message avant que l’exception ne soit levée à nouveau sur le site d’appel client.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Retours

<xref:System.Exception>  
Cette instance de l'objet <xref:System.Exception>.

## <a name="remarks"></a>Remarques

> [!WARNING]
> La `Exception.PrepForRemoting` méthode est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System>

**Assembly :** mscorlib.dll (dans mscorlib.dll)

**Versions de .NET Framework :** Disponible depuis 1,0.
