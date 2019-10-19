---
title: Méthode XmlReader. CreateSqlReader (System. Xml)
author: mairaw
ms.author: mairaw
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 302be4eff32d2c96a1571d291e0b289e77694db8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584133"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="0a06e-102">Méthode XmlReader. CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="0a06e-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="0a06e-103">Crée une instance de <xref:System.Xml.XmlReader> à l’aide du flux, des paramètres et des informations de contexte d’analyse spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0a06e-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="0a06e-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a06e-104">Parameters</span></span>

- <span data-ttu-id="0a06e-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="0a06e-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="0a06e-106">Flux contenant les données XML.</span><span class="sxs-lookup"><span data-stu-id="0a06e-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="0a06e-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="0a06e-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="0a06e-108">Paramètres de la nouvelle instance de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="0a06e-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="0a06e-109">Cette valeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="0a06e-109">This value can be `null`.</span></span>

- <span data-ttu-id="0a06e-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="0a06e-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="0a06e-111">Les informations de contexte nécessaires à l'analyse du fragment XML.</span><span class="sxs-lookup"><span data-stu-id="0a06e-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="0a06e-112">Cette valeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="0a06e-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="0a06e-113">Returns (Retours)</span><span class="sxs-lookup"><span data-stu-id="0a06e-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="0a06e-114">Objet permettant de lire les données XML contenues dans le flux de données.</span><span class="sxs-lookup"><span data-stu-id="0a06e-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a06e-115">Notes</span><span class="sxs-lookup"><span data-stu-id="0a06e-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0a06e-116">La méthode `XmlReader.CreateSqlReader` est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="0a06e-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0a06e-117">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="0a06e-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a06e-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="0a06e-118">Requirements</span></span>

<span data-ttu-id="0a06e-119">**Espace de noms :** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="0a06e-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="0a06e-120">**Assembly :** System. Xml. dll</span><span class="sxs-lookup"><span data-stu-id="0a06e-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="0a06e-121">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="0a06e-121">**.NET Framework versions:** Available since 2.0.</span></span>
