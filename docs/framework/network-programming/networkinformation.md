---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 550555be7cc95cafebabfd3ac230ced024a9202c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261616"
---
# <a name="networkinformation"></a><span data-ttu-id="9fcfb-102">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="9fcfb-102">NetworkInformation</span></span>

<span data-ttu-id="9fcfb-103">L’espace de noms <xref:System.Net.NetworkInformation> permet de recueillir des informations concernant les événements, les modifications, les statistiques et les propriétés liés au réseau.</span><span class="sxs-lookup"><span data-stu-id="9fcfb-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="9fcfb-104">Vous pouvez également déterminer si un hôte distant est accessible à l’aide de la classe <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9fcfb-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="9fcfb-105">Disponibilité du réseau et événements réseau</span><span class="sxs-lookup"><span data-stu-id="9fcfb-105">Network Availability and Events</span></span>  

 <span data-ttu-id="9fcfb-106">La classe <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> permet de déterminer si l’adresse réseau ou la disponibilité du réseau ont changé.</span><span class="sxs-lookup"><span data-stu-id="9fcfb-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="9fcfb-107">Pour utiliser cette classe, créez un gestionnaire d’événements en vue de traiter la modification, puis associez-la à un <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> ou un <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9fcfb-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="9fcfb-108">Pour plus d’informations, consultez [Guide pratique pour détecter la disponibilité réseau et les changements d’adresse](how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="9fcfb-108">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="9fcfb-109">Statistiques et propriétés du réseau</span><span class="sxs-lookup"><span data-stu-id="9fcfb-109">Network Statistics and Properties</span></span>  

 <span data-ttu-id="9fcfb-110">Vous pouvez collecter des informations relatives aux statistiques et aux propriétés du réseau au niveau d’une interface ou d’un protocole.</span><span class="sxs-lookup"><span data-stu-id="9fcfb-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="9fcfb-111">Les classes <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType> et <xref:System.Net.NetworkInformation.PhysicalAddress> fournissent des informations sur les interfaces réseau, alors que les classes <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics> et <xref:System.Net.NetworkInformation.UdpStatistics> fournissent des informations sur les paquets des couches 3 et 4.</span><span class="sxs-lookup"><span data-stu-id="9fcfb-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="9fcfb-112">Pour plus d’informations, consultez [Guide pratique pour obtenir des informations d’interface et de protocole](how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="9fcfb-112">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="9fcfb-113">Déterminer si un hôte distant est accessible</span><span class="sxs-lookup"><span data-stu-id="9fcfb-113">Determine if a Remote Host is Reachable</span></span>  

 <span data-ttu-id="9fcfb-114">Vous pouvez utiliser la classe <xref:System.Net.NetworkInformation.Ping> pour déterminer si un hôte distant est disponible, s’il se trouve dans le réseau et s’il est accessible.</span><span class="sxs-lookup"><span data-stu-id="9fcfb-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="9fcfb-115">Pour plus d’informations, consultez [Guide pratique pour effectuer un test ping](how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="9fcfb-115">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fcfb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fcfb-116">See also</span></span>

- [<span data-ttu-id="9fcfb-117">Exemples de programmation réseau</span><span class="sxs-lookup"><span data-stu-id="9fcfb-117">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
