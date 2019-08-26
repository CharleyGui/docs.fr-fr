---
title: 'Procédure : modifier le fichier config de l’ordinateur en vue d’activer la prise en charge IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: af6eb8a334108c988967a555024b524e27d40f58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959076"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="ea065-102">Procédure : modifier le fichier config de l’ordinateur en vue d’activer la prise en charge IPv6</span><span class="sxs-lookup"><span data-stu-id="ea065-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="ea065-103">L’exemple de code suivant montre comment modifier le fichier de configuration (*machine.config*) d’un ordinateur pour activer la prise en charge d’IPv6.</span><span class="sxs-lookup"><span data-stu-id="ea065-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="ea065-104">Le fichier *machine.config* est stocké dans le dossier *%Windir%\Microsoft.NET\Framework*, situé dans le répertoire d’installation de Windows.</span><span class="sxs-lookup"><span data-stu-id="ea065-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="ea065-105">Il y a un fichier *machine.config* distinct dans les dossiers sous *%Windir%\Microsoft.NET\Framework* pour chaque version de .NET Framework installée sur l’ordinateur (par exemple, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="ea065-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="ea065-106">Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ea065-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="ea065-107">Pour .NET Framework version 1.1 ou antérieure, la valeur du commutateur de configuration **ipv6 enabled** spécifie si les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType> retournent des adresses IPv6.</span><span class="sxs-lookup"><span data-stu-id="ea065-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="ea065-108">Pour .NET Framework version 2.0 ou ultérieure, si Windows prend en charge le protocole IPv6, tous les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType> (par exemple, la méthode <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>) retournent des adresses IPv6 avec une limitation.</span><span class="sxs-lookup"><span data-stu-id="ea065-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="ea065-109">Les membres obsolètes de la classe <xref:System.Net.Dns?displayProperty=nameWithType> (par exemple, la méthode <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) lisent et reconnaissent la valeur dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ea065-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea065-110">Pour .NET Framework version 2.0 ou ultérieure, IPv6 est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea065-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="ea065-111">Pour .NET Framework version 1.1 ou antérieure, IPv6 est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea065-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea065-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="ea065-112">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea065-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea065-113">See also</span></span>

- [<span data-ttu-id="ea065-114">Adressage IPv6</span><span class="sxs-lookup"><span data-stu-id="ea065-114">IPv6 Addressing</span></span>](../../../docs/framework/network-programming/ipv6-addressing.md)
- [<span data-ttu-id="ea065-115">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="ea065-115">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="ea065-116">\<ipv6>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="ea065-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
