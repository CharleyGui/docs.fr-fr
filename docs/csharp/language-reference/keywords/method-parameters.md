---
description: Paramètres de méthode - Référence C#
title: Paramètres de méthode - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 7090bf1c3df65cf1e65942404f883b49612e7521
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134404"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="60b7e-103">Paramètres de méthode (référence C#)</span><span class="sxs-lookup"><span data-stu-id="60b7e-103">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="60b7e-104">Les paramètres déclarés pour une méthode sans [in](./in-parameter-modifier.md), [ref](./ref.md) ou [out](./out-parameter-modifier.md) sont passés à la méthode appelée par valeur.</span><span class="sxs-lookup"><span data-stu-id="60b7e-104">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="60b7e-105">Cette valeur peut être modifiée dans la méthode, mais la valeur modifiée n’est pas conservée quand le contrôle repasse à la procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="60b7e-105">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="60b7e-106">En utilisant un mot clé de paramètre de méthode, vous pouvez modifier ce comportement.</span><span class="sxs-lookup"><span data-stu-id="60b7e-106">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="60b7e-107">Cette section décrit les mots clés que vous pouvez utiliser pour déclarer des paramètres de méthode :</span><span class="sxs-lookup"><span data-stu-id="60b7e-107">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="60b7e-108">[params](./params.md) spécifie que ce paramètre peut prendre un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="60b7e-108">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="60b7e-109">[in](./in-parameter-modifier.md) spécifie que ce paramètre est passé par référence, mais qu’il est lu uniquement par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="60b7e-109">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="60b7e-110">[ref](./ref.md) spécifie que ce paramètre est passé par référence et qu’il peut être lu ou écrit par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="60b7e-110">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="60b7e-111">[out](./out-parameter-modifier.md) spécifie que ce paramètre est passé par référence et qu’il est écrit par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="60b7e-111">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="60b7e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60b7e-112">See also</span></span>

- [<span data-ttu-id="60b7e-113">Référence C#</span><span class="sxs-lookup"><span data-stu-id="60b7e-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="60b7e-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="60b7e-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="60b7e-115">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="60b7e-115">C# Keywords</span></span>](./index.md)
