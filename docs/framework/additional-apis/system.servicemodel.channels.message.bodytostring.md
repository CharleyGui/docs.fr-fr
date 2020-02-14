---
title: Méthode message. BodyToString (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215505"
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

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.ServiceModel.Channels>

**Assembly :** System. ServiceModel. dll

**Versions de .NET Framework :** Disponible depuis 3,0.
