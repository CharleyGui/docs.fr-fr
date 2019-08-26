---
title: Opérations relatives aux ports dans le .NET Framework avec Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 936ff4c861444d3a971b38fd7b2a0af38b19494b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916601"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="d984c-102">Opérations relatives aux ports dans le .NET Framework avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d984c-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="d984c-103">Vous pouvez accéder aux ports série de votre ordinateur par l’intermédiaire des classes .NET Framework dans l’espace de noms <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d984c-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d984c-104">La classe la plus importante, <xref:System.IO.Ports.SerialPort>, fournit un framework pour les E/S synchrones et pilotées par événements, l’accès aux états d’épinglage et d’arrêt, et l’accès aux propriétés des pilotes séries.</span><span class="sxs-lookup"><span data-stu-id="d984c-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="d984c-105">Elle peut être encapsulée dans un objet <xref:System.IO.Stream>, accessible par l’intermédiaire de la propriété <xref:System.IO.Ports.SerialPort.BaseStream>.</span><span class="sxs-lookup"><span data-stu-id="d984c-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="d984c-106">L’encapsulage de <xref:System.IO.Ports.SerialPort> dans un objet <xref:System.IO.Stream> permet aux classes qui utilisent des flux d’accéder au port série.</span><span class="sxs-lookup"><span data-stu-id="d984c-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="d984c-107">L’espace de noms contient des énumérations qui simplifient le contrôle des ports série.</span><span class="sxs-lookup"><span data-stu-id="d984c-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="d984c-108">Le moyen le plus simple de créer un objet <xref:System.IO.Ports.SerialPort> consiste à utiliser la méthode <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="d984c-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d984c-109">Vous ne pouvez pas utiliser les classes .NET Framework pour accéder directement aux autres types de ports, tels que les ports parallèles, les ports USB, etc.</span><span class="sxs-lookup"><span data-stu-id="d984c-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="d984c-110">Énumérations</span><span class="sxs-lookup"><span data-stu-id="d984c-110">Enumerations</span></span>  
 <span data-ttu-id="d984c-111">Ce tableau répertorie et décrit les principales énumérations utilisées pour accéder à un port série :</span><span class="sxs-lookup"><span data-stu-id="d984c-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="d984c-112">Énumération</span><span class="sxs-lookup"><span data-stu-id="d984c-112">Enumeration</span></span>|<span data-ttu-id="d984c-113">Description</span><span class="sxs-lookup"><span data-stu-id="d984c-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="d984c-114">Spécifie le protocole de contrôle utilisé pour établir une communication de port série pour un objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="d984c-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="d984c-115">Spécifie le bit de parité pour un objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="d984c-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="d984c-116">Spécifie le type de caractère qui a été reçu sur le port série de l’objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="d984c-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="d984c-117">Spécifie les erreurs qui se produisent sur l’objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="d984c-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="d984c-118">Spécifie le type de changement qui s’est produit sur l’objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="d984c-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="d984c-119">Spécifie le nombre de bits d’arrêt utilisés sur l’objet <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="d984c-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d984c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d984c-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="d984c-121">Accès aux ports de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="d984c-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
