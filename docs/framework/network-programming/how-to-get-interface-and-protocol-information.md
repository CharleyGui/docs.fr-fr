---
title: 'Comment : obtenir des informations d’interface et de protocole'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: fd88d26c-4063-495e-a253-736ac3e6b23f
ms.openlocfilehash: b2b2f4f0bfa8b026bbd5dce8e25919a4a7fc7036
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180820"
---
# <a name="how-to-get-interface-and-protocol-information"></a><span data-ttu-id="c97d8-102">Comment : obtenir des informations d’interface et de protocole</span><span class="sxs-lookup"><span data-stu-id="c97d8-102">How to: Get Interface and Protocol Information</span></span>
<span data-ttu-id="c97d8-103">Cet exemple montre comment lire les statistiques TCP d’une interface réseau.</span><span class="sxs-lookup"><span data-stu-id="c97d8-103">This sample shows how to read the TCP statistics of a network interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c97d8-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c97d8-104">Example</span></span>  
  
```csharp
public static void ShowTcpStatistics(NetworkInterfaceComponent version)  
{  
    IPGlobalProperties properties =  
          IPGlobalProperties.GetIPGlobalProperties();  
    TcpStatistics tcpstat = null;  
    Console.WriteLine("");  
    switch (version)  
    {  
        case NetworkInterfaceComponent.IPv4:  
             tcpstat = properties.GetTcpIPv4Statistics();  
            Console.WriteLine("TCP/IPv4 Statistics:");  
            break;  
        case NetworkInterfaceComponent.IPv6:  
            tcpstat = properties.GetTcpIPv6Statistics();  
            Console.WriteLine("TCP/IPv6 Statistics:");  
            break;  
        default:  
            throw new ArgumentException("version");  
            break;  
    }  
    Console.WriteLine("  Minimum Transmission Timeout. : {0}",
        tcpstat.MinimumTransmissionTimeout);  
    Console.WriteLine("  Maximum Transmission Timeout. : {0}",
        tcpstat.MaximumTransmissionTimeout);  
  
    Console.WriteLine("  Connection Data:");  
    Console.WriteLine("      Current : {0}",
    tcpstat.CurrentConnections);  
    Console.WriteLine("      Cumulative : {0}",
        tcpstat.CumulativeConnections);  
    Console.WriteLine("      Initiated  : {0}",
        tcpstat.ConnectionsInitiated);  
    Console.WriteLine("      Accepted : {0}",
        tcpstat.ConnectionsAccepted);  
    Console.WriteLine("      Failed Attempts : {0}",
        tcpstat.FailedConnectionAttempts);  
    Console.WriteLine("      Reset : {0}",
        tcpstat.ResetConnections);  
  
    Console.WriteLine("");  
    Console.WriteLine("  Segment Data:");  
    Console.WriteLine("      Received  ................... : {0}",
        tcpstat.SegmentsReceived);  
    Console.WriteLine("      Sent : {0}",
        tcpstat.SegmentsSent);  
    Console.WriteLine("      Retransmitted : {0}",
        tcpstat.SegmentsResent);  
  
    Console.WriteLine("");  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c97d8-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c97d8-105">Compiling the Code</span></span>  
 <span data-ttu-id="c97d8-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="c97d8-106">This example requires:</span></span>  
  
- <span data-ttu-id="c97d8-107">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="c97d8-107">References to the **System.Net** namespace.</span></span>
