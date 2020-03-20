---
title: Activation et désactivation d’IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048561"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="653ba-102">Activation et désactivation d’IPv6</span><span class="sxs-lookup"><span data-stu-id="653ba-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="653ba-103">Pour utiliser le protocole IPv6, vérifiez que vous exécutez une version du système d’exploitation qui prend en charge IPv6 et que le système d’exploitation et les classes de mise en réseau sont configurés correctement.</span><span class="sxs-lookup"><span data-stu-id="653ba-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="653ba-104">Étapes de configuration</span><span class="sxs-lookup"><span data-stu-id="653ba-104">Configuration Steps</span></span>  
 <span data-ttu-id="653ba-105">Le tableau suivant répertorie les différentes configurations</span><span class="sxs-lookup"><span data-stu-id="653ba-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="653ba-106">Système d’exploitation compatible avec IPv6 ?</span><span class="sxs-lookup"><span data-stu-id="653ba-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="653ba-107">Classes de mise en réseau compatibles avec IPv6 ?</span><span class="sxs-lookup"><span data-stu-id="653ba-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="653ba-108">Description</span><span class="sxs-lookup"><span data-stu-id="653ba-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="653ba-109">Non </span><span class="sxs-lookup"><span data-stu-id="653ba-109">No</span></span>|<span data-ttu-id="653ba-110">Non </span><span class="sxs-lookup"><span data-stu-id="653ba-110">No</span></span>|<span data-ttu-id="653ba-111">Peut analyser les adresses IPv6.</span><span class="sxs-lookup"><span data-stu-id="653ba-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="653ba-112">Non </span><span class="sxs-lookup"><span data-stu-id="653ba-112">No</span></span>|<span data-ttu-id="653ba-113">Oui</span><span class="sxs-lookup"><span data-stu-id="653ba-113">Yes</span></span>|<span data-ttu-id="653ba-114">Peut analyser les adresses IPv6.</span><span class="sxs-lookup"><span data-stu-id="653ba-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="653ba-115">Oui</span><span class="sxs-lookup"><span data-stu-id="653ba-115">Yes</span></span>|<span data-ttu-id="653ba-116">Non </span><span class="sxs-lookup"><span data-stu-id="653ba-116">No</span></span>|<span data-ttu-id="653ba-117">Peut analyser les adresses IPv6 et résoudre les adresses IPv6 à l’aide des méthodes de résolution de noms qui ne sont pas marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="653ba-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="653ba-118">Oui</span><span class="sxs-lookup"><span data-stu-id="653ba-118">Yes</span></span>|<span data-ttu-id="653ba-119">Oui</span><span class="sxs-lookup"><span data-stu-id="653ba-119">Yes</span></span>|<span data-ttu-id="653ba-120">Peut analyser et résoudre les adresses IPv6 à l’aide de toutes les méthodes, notamment celles marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="653ba-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="653ba-121">Notez que pour activer la prise en charge du protocole IPv6 pour toutes les classes dans l’espace de noms System.Net, vous devez modifier le fichier de configuration d’ordinateur ou le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="653ba-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="653ba-122">Le fichier de configuration pour une application est prioritaire par rapport au fichier de configuration d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="653ba-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="653ba-123">Pour obtenir un exemple illustrant comment modifier le fichier de configuration d’ordinateur, *machine.config*, pour activer la prise en charge du protocole Ipv6, consultez [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md) (Guide pratique pour modifier le fichier de configuration d’ordinateur pour activer la prise en charge du protocole IPv6).</span><span class="sxs-lookup"><span data-stu-id="653ba-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="653ba-124">Vérifiez également que la prise en charge du protocole IPv6 est activée pour le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="653ba-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="653ba-125">Le .NET Framework a un commutateur de configuration défini dans un fichier de configuration comme suit :</span><span class="sxs-lookup"><span data-stu-id="653ba-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 <span data-ttu-id="653ba-126">Pour le .NET Framework version 1.1 et antérieures, la valeur du commutateur de configuration **ipv6 enabled** spécifie si les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType> retournent des adresses IPv6.</span><span class="sxs-lookup"><span data-stu-id="653ba-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="653ba-127">Pour le .NET Framework version 2.0 et ultérieures, si Windows prend en charge le protocole IPv6, les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType>, (par exemple la méthode <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>), retournent des adresses IPv6 avec une limitation.</span><span class="sxs-lookup"><span data-stu-id="653ba-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="653ba-128">Les membres obsolètes du <xref:System.Net.Dns?displayProperty=nameWithType> DNS (par exemple la méthode <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) lisent et reconnaissent la valeur dans le fichier de configuration pour le paramètre ipv6 enabled.</span><span class="sxs-lookup"><span data-stu-id="653ba-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653ba-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="653ba-129">See also</span></span>

- [<span data-ttu-id="653ba-130">Version 6 du protocole Internet</span><span class="sxs-lookup"><span data-stu-id="653ba-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="653ba-131">Sockets</span><span class="sxs-lookup"><span data-stu-id="653ba-131">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="653ba-132">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="653ba-132">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="653ba-133">\<ipv6> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="653ba-133">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
