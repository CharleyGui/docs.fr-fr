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
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="6c852-102">XmlReader.CreateSqlReader, méthode</span><span class="sxs-lookup"><span data-stu-id="6c852-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="6c852-103">Crée une instance de <xref:System.Xml.XmlReader> à l’aide du flux, des paramètres et des informations de contexte d’analyse spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6c852-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="6c852-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6c852-104">Parameters</span></span>

- <span data-ttu-id="6c852-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="6c852-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="6c852-106">Flux contenant les données XML.</span><span class="sxs-lookup"><span data-stu-id="6c852-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="6c852-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="6c852-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="6c852-108">Paramètres de la nouvelle instance de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="6c852-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="6c852-109">Cette valeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="6c852-109">This value can be `null`.</span></span>

- <span data-ttu-id="6c852-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="6c852-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="6c852-111">Les informations de contexte nécessaires à l'analyse du fragment XML.</span><span class="sxs-lookup"><span data-stu-id="6c852-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="6c852-112">Cette valeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="6c852-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="6c852-113">Retours</span><span class="sxs-lookup"><span data-stu-id="6c852-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="6c852-114">Objet permettant de lire les données XML contenues dans le flux de données.</span><span class="sxs-lookup"><span data-stu-id="6c852-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c852-115">Notes </span><span class="sxs-lookup"><span data-stu-id="6c852-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6c852-116">La `XmlReader.CreateSqlReader` méthode est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="6c852-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6c852-117">Microsoft ne prend en charge l’utilisation de cette méthode dans une application de production en aucune circonstance.</span><span class="sxs-lookup"><span data-stu-id="6c852-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6c852-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6c852-118">Requirements</span></span>

<span data-ttu-id="6c852-119">**Espace nom:**<xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="6c852-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="6c852-120">**Assemblée:** System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="6c852-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="6c852-121">**.NET Versions du Cadre:** Disponible depuis 2.0.</span><span class="sxs-lookup"><span data-stu-id="6c852-121">**.NET Framework versions:** Available since 2.0.</span></span>
