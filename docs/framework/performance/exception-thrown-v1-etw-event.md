---
title: Événement ETW d'exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716050"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="88127-102">Événement ETW d'exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="88127-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="88127-103">Cet événement capture des informations sur les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="88127-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="88127-104">Le tableau suivant affiche le mot clé sous lequel l’événement est déclenché, ainsi que le niveau de l’événement.</span><span class="sxs-lookup"><span data-stu-id="88127-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="88127-105">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="88127-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="88127-106">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="88127-106">Keyword for raising the event</span></span>|<span data-ttu-id="88127-107">Niveau</span><span class="sxs-lookup"><span data-stu-id="88127-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="88127-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="88127-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="88127-109">Avertissement (2)</span><span class="sxs-lookup"><span data-stu-id="88127-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="88127-110">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="88127-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="88127-111">Event</span><span class="sxs-lookup"><span data-stu-id="88127-111">Event</span></span>|<span data-ttu-id="88127-112">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="88127-112">Event ID</span></span>|<span data-ttu-id="88127-113">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="88127-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="88127-114">80</span><span class="sxs-lookup"><span data-stu-id="88127-114">80</span></span>|<span data-ttu-id="88127-115">Une exception managée est levée.</span><span class="sxs-lookup"><span data-stu-id="88127-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="88127-116">Le tableau suivant affiche des données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="88127-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="88127-117">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="88127-117">Field name</span></span>|<span data-ttu-id="88127-118">Type de données</span><span class="sxs-lookup"><span data-stu-id="88127-118">Data type</span></span>|<span data-ttu-id="88127-119">Description</span><span class="sxs-lookup"><span data-stu-id="88127-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="88127-120">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="88127-120">Exception Type</span></span>|<span data-ttu-id="88127-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="88127-121">win:UnicodeString</span></span>|<span data-ttu-id="88127-122">Type de l’exception, par exemple `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="88127-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="88127-123">Message d’exception</span><span class="sxs-lookup"><span data-stu-id="88127-123">Exception Message</span></span>|<span data-ttu-id="88127-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="88127-124">win:UnicodeString</span></span>|<span data-ttu-id="88127-125">Message d’exception réel.</span><span class="sxs-lookup"><span data-stu-id="88127-125">Actual exception message.</span></span>|  
|<span data-ttu-id="88127-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="88127-126">EIPCodeThrow</span></span>|<span data-ttu-id="88127-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="88127-127">win:Pointer</span></span>|<span data-ttu-id="88127-128">Pointeur d’instruction où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="88127-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="88127-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="88127-129">ExceptionHR</span></span>|<span data-ttu-id="88127-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="88127-130">win:UInt32</span></span>|<span data-ttu-id="88127-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="88127-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="88127-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="88127-132">ExceptionFlags</span></span>|<span data-ttu-id="88127-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="88127-133">win:UInt16</span></span>|<span data-ttu-id="88127-134">0x01 : HasInnerException (consultez [Événements ETW du CLR](clr-etw-events.md) dans la documentation Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="88127-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="88127-135">0x02 : IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="88127-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="88127-136">0x04 : IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="88127-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="88127-137">0x08 : IsCorruptedStateException (indique que l’état du processus est endommagé ; consultez [gestion des exceptions d’état endommagé](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="88127-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="88127-138">0x10 : IsCLSCompliant (une exception qui dérive d’<xref:System.Exception> est conforme CLS ; sinon elle n’est pas conforme CLS).</span><span class="sxs-lookup"><span data-stu-id="88127-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="88127-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="88127-139">ClrInstanceID</span></span>|<span data-ttu-id="88127-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="88127-140">win:UInt16</span></span>|<span data-ttu-id="88127-141">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="88127-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88127-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88127-142">See also</span></span>

- [<span data-ttu-id="88127-143">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="88127-143">CLR ETW Events</span></span>](clr-etw-events.md)
