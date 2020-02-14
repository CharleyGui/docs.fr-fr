---
title: Méthode XmlReader. CreateSqlReader (System. Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: c65ef7c073175488c11c5e912a44d46fd4319209
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215448"
---
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader, méthode

Crée une instance de <xref:System.Xml.XmlReader> à l’aide du flux, des paramètres et des informations de contexte d’analyse spécifiés.

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Paramètres

- `input` <xref:System.IO.Stream>  
  Flux contenant les données XML.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  Paramètres de la nouvelle instance de <xref:System.Xml.XmlReader>. Cette valeur peut être `null`.

- `inputContext` <xref:System.Xml.XmlParserContext>  
  Les informations de contexte nécessaires à l'analyse du fragment XML. Cette valeur peut être `null`.

## <a name="returns"></a>Retours

<xref:System.Xml.XmlReader>  
Objet permettant de lire les données XML contenues dans le flux de données.

## <a name="remarks"></a>Notes

> [!WARNING]
> La méthode `XmlReader.CreateSqlReader` est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Xml>

**Assembly :** System. Xml. dll

**Versions de .NET Framework :** Disponible depuis 2,0.
