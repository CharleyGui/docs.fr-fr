---
title: Paramètres de méthode - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 4011cbd3bc9306b64df87b1fcde48f1f41df8240
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602045"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="6017f-102">Paramètres de méthode (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6017f-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="6017f-103">Les paramètres déclarés pour une méthode sans [in](./in-parameter-modifier.md), [ref](./ref.md) ou [out](./out-parameter-modifier.md) sont passés à la méthode appelée par valeur.</span><span class="sxs-lookup"><span data-stu-id="6017f-103">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="6017f-104">Cette valeur peut être modifiée dans la méthode, mais la valeur modifiée n’est pas conservée quand le contrôle repasse à la procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="6017f-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="6017f-105">En utilisant un mot clé de paramètre de méthode, vous pouvez modifier ce comportement.</span><span class="sxs-lookup"><span data-stu-id="6017f-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="6017f-106">Cette section décrit les mots clés que vous pouvez utiliser pour déclarer des paramètres de méthode :</span><span class="sxs-lookup"><span data-stu-id="6017f-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="6017f-107">[params](./params.md) spécifie que ce paramètre peut prendre un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="6017f-107">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="6017f-108">[in](./in-parameter-modifier.md) spécifie que ce paramètre est passé par référence, mais qu’il est lu uniquement par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="6017f-108">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="6017f-109">[ref](./ref.md) spécifie que ce paramètre est passé par référence et qu’il peut être lu ou écrit par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="6017f-109">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="6017f-110">[out](./out-parameter-modifier.md) spécifie que ce paramètre est passé par référence et qu’il est écrit par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="6017f-110">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6017f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6017f-111">See also</span></span>

- [<span data-ttu-id="6017f-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="6017f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6017f-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6017f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6017f-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="6017f-114">C# Keywords</span></span>](./index.md)
