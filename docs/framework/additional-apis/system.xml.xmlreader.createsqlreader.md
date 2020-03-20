---
title: XmlReader.CreateSqlReader Méthode (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 7bd2ef5158516acede47f73f9937d06159bc16c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155737"
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
> La `XmlReader.CreateSqlReader` méthode est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend en charge l’utilisation de cette méthode dans une application de production en aucune circonstance.

## <a name="requirements"></a>Spécifications

**Espace nom:**<xref:System.Xml>

**Assemblée:** System.Xml.dll

**.NET Versions du Cadre:** Disponible depuis 2.0.
