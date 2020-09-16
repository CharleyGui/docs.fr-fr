---
title: Événement ETW d'exception Thrown_V1
description: Affichez des informations détaillées sur l’événement ETW de ExceptionThrown_V1. Les données d’événement, telles que les noms de champs, les types de données et les descriptions, sont fournies pour les exceptions levées.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f4ae277b5dfb09d2676755fec2208b63906ead84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554669"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="971c4-104">Événement ETW d'exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="971c4-104">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="971c4-105">Cet événement capture des informations sur les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="971c4-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="971c4-106">Le tableau suivant affiche le mot clé sous lequel l’événement est déclenché, ainsi que le niveau de l’événement.</span><span class="sxs-lookup"><span data-stu-id="971c4-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="971c4-107">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="971c4-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="971c4-108">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="971c4-108">Keyword for raising the event</span></span>|<span data-ttu-id="971c4-109">Niveau</span><span class="sxs-lookup"><span data-stu-id="971c4-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="971c4-110">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="971c4-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="971c4-111">Avertissement (2)</span><span class="sxs-lookup"><span data-stu-id="971c4-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="971c4-112">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="971c4-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="971c4-113">Événement</span><span class="sxs-lookup"><span data-stu-id="971c4-113">Event</span></span>|<span data-ttu-id="971c4-114">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="971c4-114">Event ID</span></span>|<span data-ttu-id="971c4-115">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="971c4-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="971c4-116">80</span><span class="sxs-lookup"><span data-stu-id="971c4-116">80</span></span>|<span data-ttu-id="971c4-117">Une exception managée est levée.</span><span class="sxs-lookup"><span data-stu-id="971c4-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="971c4-118">Le tableau suivant affiche des données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="971c4-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="971c4-119">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="971c4-119">Field name</span></span>|<span data-ttu-id="971c4-120">Type de données</span><span class="sxs-lookup"><span data-stu-id="971c4-120">Data type</span></span>|<span data-ttu-id="971c4-121">Description</span><span class="sxs-lookup"><span data-stu-id="971c4-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="971c4-122">Type d’exception</span><span class="sxs-lookup"><span data-stu-id="971c4-122">Exception Type</span></span>|<span data-ttu-id="971c4-123">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="971c4-123">win:UnicodeString</span></span>|<span data-ttu-id="971c4-124">Type de l’exception, par exemple `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="971c4-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="971c4-125">Message d’exception</span><span class="sxs-lookup"><span data-stu-id="971c4-125">Exception Message</span></span>|<span data-ttu-id="971c4-126">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="971c4-126">win:UnicodeString</span></span>|<span data-ttu-id="971c4-127">Message d’exception réel.</span><span class="sxs-lookup"><span data-stu-id="971c4-127">Actual exception message.</span></span>|  
|<span data-ttu-id="971c4-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="971c4-128">EIPCodeThrow</span></span>|<span data-ttu-id="971c4-129">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="971c4-129">win:Pointer</span></span>|<span data-ttu-id="971c4-130">Pointeur d’instruction où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="971c4-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="971c4-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="971c4-131">ExceptionHR</span></span>|<span data-ttu-id="971c4-132">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="971c4-132">win:UInt32</span></span>|<span data-ttu-id="971c4-133">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="971c4-133">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="971c4-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="971c4-134">ExceptionFlags</span></span>|<span data-ttu-id="971c4-135">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="971c4-135">win:UInt16</span></span>|<span data-ttu-id="971c4-136">0x01 : HasInnerException (consultez [Événements ETW du CLR](clr-etw-events.md) dans la documentation Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="971c4-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="971c4-137">0x02 : IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="971c4-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="971c4-138">0x04 : IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="971c4-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="971c4-139">0x08 : IsCorruptedStateException (indique que l’état du processus est endommagé ; consultez [gestion des exceptions d’état endommagé](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="971c4-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="971c4-140">0x10 : IsCLSCompliant (une exception qui dérive d’<xref:System.Exception> est conforme CLS ; sinon elle n’est pas conforme CLS).</span><span class="sxs-lookup"><span data-stu-id="971c4-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="971c4-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="971c4-141">ClrInstanceID</span></span>|<span data-ttu-id="971c4-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="971c4-142">win:UInt16</span></span>|<span data-ttu-id="971c4-143">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="971c4-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="971c4-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="971c4-144">See also</span></span>

- [<span data-ttu-id="971c4-145">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="971c4-145">CLR ETW Events</span></span>](clr-etw-events.md)
