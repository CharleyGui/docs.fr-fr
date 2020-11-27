---
title: 'Procédure : Détecter la disponibilité réseau et les changements d’adresse'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: 8f5eef7b6ba41f1ac4050fbc9168fafea31b103f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287310"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="e53a7-102">Procédure : Détecter la disponibilité réseau et les changements d’adresse</span><span class="sxs-lookup"><span data-stu-id="e53a7-102">How to: Detect Network Availability and Address Changes</span></span>

<span data-ttu-id="e53a7-103">Cet exemple montre comment détecter les modifications de l’adresse réseau d’une interface.</span><span class="sxs-lookup"><span data-stu-id="e53a7-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e53a7-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e53a7-104">Example</span></span>  
  
```csharp
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e53a7-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e53a7-105">Compiling the Code</span></span>  

 <span data-ttu-id="e53a7-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="e53a7-106">This example requires:</span></span>  
  
- <span data-ttu-id="e53a7-107">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="e53a7-107">References to the **System.Net** namespace.</span></span>
