---
title: Événement ETW d'exception Thrown_V1
description: Affichez des informations détaillées sur l’événement ETW de ExceptionThrown_V1. Les données d’événement, telles que les noms de champs, les types de données et les descriptions, sont fournies pour les exceptions levées.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f800a43d0ed2a82bc51a5e3a028b5fa1870df3fb
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309454"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="580af-104">Événement ETW d'exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="580af-104">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="580af-105">Cet événement capture des informations sur les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="580af-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="580af-106">Le tableau suivant affiche le mot clé sous lequel l’événement est déclenché, ainsi que le niveau de l’événement.</span><span class="sxs-lookup"><span data-stu-id="580af-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="580af-107">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="580af-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="580af-108">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="580af-108">Keyword for raising the event</span></span>|<span data-ttu-id="580af-109">Level</span><span class="sxs-lookup"><span data-stu-id="580af-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="580af-110">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="580af-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="580af-111">Avertissement (2)</span><span class="sxs-lookup"><span data-stu-id="580af-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="580af-112">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="580af-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="580af-113">Événement</span><span class="sxs-lookup"><span data-stu-id="580af-113">Event</span></span>|<span data-ttu-id="580af-114">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="580af-114">Event ID</span></span>|<span data-ttu-id="580af-115">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="580af-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="580af-116">80</span><span class="sxs-lookup"><span data-stu-id="580af-116">80</span></span>|<span data-ttu-id="580af-117">Une exception managée est levée.</span><span class="sxs-lookup"><span data-stu-id="580af-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="580af-118">Le tableau suivant affiche des données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="580af-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="580af-119">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="580af-119">Field name</span></span>|<span data-ttu-id="580af-120">Type de données</span><span class="sxs-lookup"><span data-stu-id="580af-120">Data type</span></span>|<span data-ttu-id="580af-121">Description</span><span class="sxs-lookup"><span data-stu-id="580af-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="580af-122">Type d’exception</span><span class="sxs-lookup"><span data-stu-id="580af-122">Exception Type</span></span>|<span data-ttu-id="580af-123">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="580af-123">win:UnicodeString</span></span>|<span data-ttu-id="580af-124">Type de l’exception, par exemple `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="580af-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="580af-125">Message d’exception</span><span class="sxs-lookup"><span data-stu-id="580af-125">Exception Message</span></span>|<span data-ttu-id="580af-126">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="580af-126">win:UnicodeString</span></span>|<span data-ttu-id="580af-127">Message d’exception réel.</span><span class="sxs-lookup"><span data-stu-id="580af-127">Actual exception message.</span></span>|  
|<span data-ttu-id="580af-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="580af-128">EIPCodeThrow</span></span>|<span data-ttu-id="580af-129">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="580af-129">win:Pointer</span></span>|<span data-ttu-id="580af-130">Pointeur d’instruction où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="580af-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="580af-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="580af-131">ExceptionHR</span></span>|<span data-ttu-id="580af-132">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="580af-132">win:UInt32</span></span>|<span data-ttu-id="580af-133">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="580af-133">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="580af-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="580af-134">ExceptionFlags</span></span>|<span data-ttu-id="580af-135">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="580af-135">win:UInt16</span></span>|<span data-ttu-id="580af-136">0x01 : HasInnerException (consultez [Événements ETW du CLR](clr-etw-events.md) dans la documentation Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="580af-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="580af-137">0x02 : IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="580af-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="580af-138">0x04 : IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="580af-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="580af-139">0x08 : IsCorruptedStateException (indique que l’état du processus est endommagé ; consultez [gestion des exceptions d’état endommagé](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="580af-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="580af-140">0x10 : IsCLSCompliant (une exception qui dérive d’<xref:System.Exception> est conforme CLS ; sinon elle n’est pas conforme CLS).</span><span class="sxs-lookup"><span data-stu-id="580af-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="580af-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="580af-141">ClrInstanceID</span></span>|<span data-ttu-id="580af-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="580af-142">win:UInt16</span></span>|<span data-ttu-id="580af-143">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="580af-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="580af-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="580af-144">See also</span></span>

- [<span data-ttu-id="580af-145">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="580af-145">CLR ETW Events</span></span>](clr-etw-events.md)
