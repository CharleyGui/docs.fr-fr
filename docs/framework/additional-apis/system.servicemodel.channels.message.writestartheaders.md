---
title: Méthode message. WriteStartHeaders (System. ServiceModel. Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: a2c82ee4029c7af0396219f5ded8c999fd01d65b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451177"
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

## <a name="requirements"></a>Configuration requise

**Espace de noms :** <xref:System.ServiceModel.Channels>

**Assembly :** System. ServiceModel. dll

**Versions de .NET Framework :** Disponible depuis 3,0.
