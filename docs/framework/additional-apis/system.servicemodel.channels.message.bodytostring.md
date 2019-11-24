---
title: Message.BodyToString Method (System.ServiceModel.Channels)
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
# <a name="messagebodytostring-method"></a><span data-ttu-id="5ec06-102">Message.BodyToString Method</span><span class="sxs-lookup"><span data-stu-id="5ec06-102">Message.BodyToString Method</span></span>

<span data-ttu-id="5ec06-103">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span><span class="sxs-lookup"><span data-stu-id="5ec06-103">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="5ec06-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ec06-104">Parameters</span></span>

- <span data-ttu-id="5ec06-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="5ec06-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="5ec06-106">The writer that is used to convert the message body to a string.</span><span class="sxs-lookup"><span data-stu-id="5ec06-106">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ec06-107">Notes</span><span class="sxs-lookup"><span data-stu-id="5ec06-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="5ec06-108">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span><span class="sxs-lookup"><span data-stu-id="5ec06-108">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5ec06-109">Microsoft does not support the use of this method in a production application under any circumstance.</span><span class="sxs-lookup"><span data-stu-id="5ec06-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ec06-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="5ec06-110">Requirements</span></span>

<span data-ttu-id="5ec06-111">**Espace de noms :** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="5ec06-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="5ec06-112">**Assembly:** System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="5ec06-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="5ec06-113">**.NET Framework versions:** Available since 3.0.</span><span class="sxs-lookup"><span data-stu-id="5ec06-113">**.NET Framework versions:** Available since 3.0.</span></span>
