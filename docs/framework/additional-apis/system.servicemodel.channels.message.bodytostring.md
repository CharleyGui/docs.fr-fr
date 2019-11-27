---
title: Méthode message. BodyToString (System. ServiceModel. Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 7b0b56bfda1c0c37f43f95e9684d3b4042c1b97c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451205"
---
# <a name="messagebodytostring-method"></a>Méthode message. BodyToString

Convertit le corps du message en une chaîne en appelant la méthode <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType>.

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>Paramètres

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  Writer utilisé pour convertir le corps du message en une chaîne.

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `Message.BodyToString` est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Configuration requise

**Espace de noms :** <xref:System.ServiceModel.Channels>

**Assembly :** System. ServiceModel. dll

**Versions de .NET Framework :** Disponible depuis 3,0.
