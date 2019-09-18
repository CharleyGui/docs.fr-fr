---
title: Événement ETW d'exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91abd9e6f31380b7e8cd3df1a14aa5c5722901ba
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046515"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="63737-102">Événement ETW d'exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="63737-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="63737-103">Cet événement capture des informations sur les exceptions levées.</span><span class="sxs-lookup"><span data-stu-id="63737-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="63737-104">Le tableau suivant affiche le mot clé sous lequel l’événement est déclenché, ainsi que le niveau de l’événement.</span><span class="sxs-lookup"><span data-stu-id="63737-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="63737-105">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="63737-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="63737-106">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="63737-106">Keyword for raising the event</span></span>|<span data-ttu-id="63737-107">Niveau</span><span class="sxs-lookup"><span data-stu-id="63737-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="63737-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="63737-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="63737-109">Avertissement (2)</span><span class="sxs-lookup"><span data-stu-id="63737-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="63737-110">Le tableau suivant affiche des informations sur les événements.</span><span class="sxs-lookup"><span data-stu-id="63737-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="63737-111">Événement</span><span class="sxs-lookup"><span data-stu-id="63737-111">Event</span></span>|<span data-ttu-id="63737-112">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="63737-112">Event ID</span></span>|<span data-ttu-id="63737-113">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="63737-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="63737-114">80</span><span class="sxs-lookup"><span data-stu-id="63737-114">80</span></span>|<span data-ttu-id="63737-115">Une exception managée est levée.</span><span class="sxs-lookup"><span data-stu-id="63737-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="63737-116">Le tableau suivant affiche des données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="63737-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="63737-117">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="63737-117">Field name</span></span>|<span data-ttu-id="63737-118">Type de données</span><span class="sxs-lookup"><span data-stu-id="63737-118">Data type</span></span>|<span data-ttu-id="63737-119">Description</span><span class="sxs-lookup"><span data-stu-id="63737-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="63737-120">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="63737-120">Exception Type</span></span>|<span data-ttu-id="63737-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="63737-121">win:UnicodeString</span></span>|<span data-ttu-id="63737-122">Type de l’exception, par exemple `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="63737-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="63737-123">Message d’exception</span><span class="sxs-lookup"><span data-stu-id="63737-123">Exception Message</span></span>|<span data-ttu-id="63737-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="63737-124">win:UnicodeString</span></span>|<span data-ttu-id="63737-125">Message d’exception réel.</span><span class="sxs-lookup"><span data-stu-id="63737-125">Actual exception message.</span></span>|  
|<span data-ttu-id="63737-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="63737-126">EIPCodeThrow</span></span>|<span data-ttu-id="63737-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="63737-127">win:Pointer</span></span>|<span data-ttu-id="63737-128">Pointeur d’instruction où l’exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="63737-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="63737-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="63737-129">ExceptionHR</span></span>|<span data-ttu-id="63737-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="63737-130">win:UInt32</span></span>|<span data-ttu-id="63737-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="63737-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="63737-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="63737-132">ExceptionFlags</span></span>|<span data-ttu-id="63737-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="63737-133">win:UInt16</span></span>|<span data-ttu-id="63737-134">0x01 HasInnerException (consultez [événements ETW du CLR](clr-etw-events.md) dans la documentation Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="63737-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="63737-135">0x02 IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="63737-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="63737-136">0x04 IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="63737-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="63737-137">0x08 IsCorruptedStateException (indique que l’état du processus est endommagé ; consultez [gestion des exceptions d’état endommagé](https://go.microsoft.com/fwlink/?LinkId=179681) sur MSDN).</span><span class="sxs-lookup"><span data-stu-id="63737-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="63737-138">0x10 IsCLSCompliant (une exception qui dérive de <xref:System.Exception> est conforme CLS ; sinon, elle n’est pas conforme CLS).</span><span class="sxs-lookup"><span data-stu-id="63737-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="63737-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="63737-139">ClrInstanceID</span></span>|<span data-ttu-id="63737-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="63737-140">win:UInt16</span></span>|<span data-ttu-id="63737-141">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="63737-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63737-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63737-142">See also</span></span>

- [<span data-ttu-id="63737-143">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="63737-143">CLR ETW Events</span></span>](clr-etw-events.md)
