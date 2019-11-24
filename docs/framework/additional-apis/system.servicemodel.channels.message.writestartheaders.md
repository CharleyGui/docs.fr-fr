---
title: Message.WriteStartHeaders Method (System.ServiceModel.Channels)
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
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="86f5d-102">Message.WriteStartHeaders Method</span><span class="sxs-lookup"><span data-stu-id="86f5d-102">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="86f5d-103">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span><span class="sxs-lookup"><span data-stu-id="86f5d-103">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="86f5d-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86f5d-104">Parameters</span></span>

- <span data-ttu-id="86f5d-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="86f5d-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="86f5d-106">The writer that is used to write the start header into an XML file.</span><span class="sxs-lookup"><span data-stu-id="86f5d-106">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="86f5d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="86f5d-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="86f5d-108">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span><span class="sxs-lookup"><span data-stu-id="86f5d-108">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="86f5d-109">Microsoft does not support the use of this method in a production application under any circumstance.</span><span class="sxs-lookup"><span data-stu-id="86f5d-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="86f5d-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="86f5d-110">Requirements</span></span>

<span data-ttu-id="86f5d-111">**Espace de noms :** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="86f5d-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="86f5d-112">**Assembly:** System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="86f5d-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="86f5d-113">**.NET Framework versions:** Available since 3.0.</span><span class="sxs-lookup"><span data-stu-id="86f5d-113">**.NET Framework versions:** Available since 3.0.</span></span>
