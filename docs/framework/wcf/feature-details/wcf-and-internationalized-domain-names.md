---
title: WCF et IDN (Internationalized Domain Names)
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: 2d93bbb0c284c2227a4d03acf1ad9a801df57bd8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281987"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="098d2-102">WCF et IDN (Internationalized Domain Names)</span><span class="sxs-lookup"><span data-stu-id="098d2-102">WCF and Internationalized Domain Names</span></span>

<span data-ttu-id="098d2-103">La prise en charge a été ajoutée pour tenir compte des services WCF avec des noms IDN (Internationalized Domain Names).</span><span class="sxs-lookup"><span data-stu-id="098d2-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="098d2-104">Un nom de domaine international est un nom de domaine qui contient des caractères non ASCII.</span><span class="sxs-lookup"><span data-stu-id="098d2-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="098d2-105">Cette prise en charge inclut la capacité d'héberger un service WCF avec un nom IDN et un client WCF pour parler à un service Web avec un nom IDN.</span><span class="sxs-lookup"><span data-stu-id="098d2-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="098d2-106">System.Uri et IDN</span><span class="sxs-lookup"><span data-stu-id="098d2-106">System.Uri and IDN</span></span>  

 <span data-ttu-id="098d2-107"><xref:System.Uri> contient deux propriétés : <xref:System.Uri.Host%2A> et <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="098d2-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="098d2-108">Ces propriétés contiennent des valeurs Unicode ou Punycode en fonction des paramètres de configuration pour IDN.</span><span class="sxs-lookup"><span data-stu-id="098d2-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="098d2-109">L'IDN est activé dans le fichier de configuration d'une application à l'aide du XML suivant</span><span class="sxs-lookup"><span data-stu-id="098d2-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="098d2-110">L' \<idn> élément contient l’attribut activé qui peut être défini sur l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="098d2-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1. <span data-ttu-id="098d2-111">"None"</span><span class="sxs-lookup"><span data-stu-id="098d2-111">"None"</span></span>  
  
2. <span data-ttu-id="098d2-112">AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="098d2-112">"AllExceptIntranet"</span></span>  
  
3. <span data-ttu-id="098d2-113">« Toutes »</span><span class="sxs-lookup"><span data-stu-id="098d2-113">"All"</span></span>  
  
 <span data-ttu-id="098d2-114">Lorsque le paramètre IDN a la valeur « None », aucune conversion n’est effectuée par Uri. Host ou URI. DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="098d2-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="098d2-115">Lorsque le paramètre IDN a la valeur « All », Uri. L’hôte reste Unicode et l’URI. DnsSafeHost est converti en Punycode.</span><span class="sxs-lookup"><span data-stu-id="098d2-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="098d2-116">Lorsque le paramètre IDN a la valeur « AllExceptIntranet », Uri. DnsSafeHost est converti en Punycode pour les adresses Internet et reste Unicode pour les adresses intranet.</span><span class="sxs-lookup"><span data-stu-id="098d2-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="098d2-117">Ce paramètre est important pour la résolution de noms DNS correcte.</span><span class="sxs-lookup"><span data-stu-id="098d2-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="098d2-118">Notez qu'il n'est pas nécessaire de configurer ce paramètres pour Windows 8 et les versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="098d2-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="098d2-119">Vous ne devez jamais coder une adresse en dur à l'aide de Punycode.</span><span class="sxs-lookup"><span data-stu-id="098d2-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="098d2-120">WCF le convertit pour vous en fonction des paramètres de configuration que vous appliquez.</span><span class="sxs-lookup"><span data-stu-id="098d2-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="098d2-121">Lorsque vous ajoutez des caractères Unicode à applicationHost.exe.config, enregistrez le fichier à l'aide de l'encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="098d2-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098d2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="098d2-122">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
