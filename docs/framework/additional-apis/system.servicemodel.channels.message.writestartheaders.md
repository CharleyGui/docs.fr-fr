---
title: Méthode message. WriteStartHeaders (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214863"
---
# <a name="messagewritestartheaders-method"></a>Méthode message. WriteStartHeaders

Écrit l’en-tête de début dans un fichier XML en appelant la méthode <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType>.

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>Paramètres

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  Writer utilisé pour écrire l’en-tête de début dans un fichier XML.

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `Message.WriteStartHeaders` est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.ServiceModel.Channels>

**Assembly :** System. ServiceModel. dll

**Versions de .NET Framework :** Disponible depuis 3,0.
