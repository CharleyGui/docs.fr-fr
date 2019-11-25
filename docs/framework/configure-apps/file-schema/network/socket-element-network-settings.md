---
title: <socket>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 0e2b369eccfbc658a790ef61a961315a88361669
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089088"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="58e34-102">Élément \<> Socket (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="58e34-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="58e34-103">Spécifie si les opérations de socket utilisent des ports de terminaison.</span><span class="sxs-lookup"><span data-stu-id="58e34-103">Specifies whether socket operations use completion ports.</span></span>  

<span data-ttu-id="58e34-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="58e34-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="58e34-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="58e34-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="58e34-106">&nbsp;&nbsp;&nbsp;&nbsp;[**paramètres**](settings-element-network-settings.md)\<</span><span class="sxs-lookup"><span data-stu-id="58e34-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\</span></span>
<span data-ttu-id="58e34-107">&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="58e34-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**</span></span>

## <a name="syntax"></a><span data-ttu-id="58e34-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58e34-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58e34-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="58e34-109">Attributes and Elements</span></span>  
 <span data-ttu-id="58e34-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="58e34-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58e34-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="58e34-111">Attributes</span></span>  
  
|<span data-ttu-id="58e34-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="58e34-112">**Attribute**</span></span>|<span data-ttu-id="58e34-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="58e34-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="58e34-114">Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode Accept.</span><span class="sxs-lookup"><span data-stu-id="58e34-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="58e34-115">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="58e34-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="58e34-116">Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode Connect.</span><span class="sxs-lookup"><span data-stu-id="58e34-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="58e34-117">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="58e34-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="58e34-118">Spécifie le <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> par défaut à utiliser pour un Socket.</span><span class="sxs-lookup"><span data-stu-id="58e34-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="58e34-119">La valeur par défaut dépend de la version de Windows.</span><span class="sxs-lookup"><span data-stu-id="58e34-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58e34-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="58e34-120">Child Elements</span></span>  
 <span data-ttu-id="58e34-121">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="58e34-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58e34-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="58e34-122">Parent Elements</span></span>  
  
|<span data-ttu-id="58e34-123">**Élément**</span><span class="sxs-lookup"><span data-stu-id="58e34-123">**Element**</span></span>|<span data-ttu-id="58e34-124">**Description**</span><span class="sxs-lookup"><span data-stu-id="58e34-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="58e34-125">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58e34-125">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="58e34-126">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="58e34-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58e34-127">Notes</span><span class="sxs-lookup"><span data-stu-id="58e34-127">Remarks</span></span>  
 <span data-ttu-id="58e34-128">Les attributs `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` sont utilisés pour spécifier le comportement par défaut en ce qui concerne l’utilisation des ports de terminaison par les classes de l’espace de noms <xref:System.Net.Sockets?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58e34-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="58e34-129">Les ports de terminaison sont recommandés pour les applications serveur hautes performances.</span><span class="sxs-lookup"><span data-stu-id="58e34-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="58e34-130">La valeur par défaut pour les attributs `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` est **false**.</span><span class="sxs-lookup"><span data-stu-id="58e34-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="58e34-131">Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> peut être utilisé pour récupérer la valeur actuelle de l’attribut `alwaysUseCompletionPortsForAccept` à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="58e34-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="58e34-132">Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> peut être utilisé pour récupérer la valeur actuelle de l’attribut `alwaysUseCompletionPortsForConnect` à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="58e34-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="58e34-133">L’attribut `ipProtectionLevel` spécifie la <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> par défaut à utiliser pour un Socket.</span><span class="sxs-lookup"><span data-stu-id="58e34-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="58e34-134">La propriété <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> permet la configuration d’une restriction pour un socket IPv6 à une étendue spécifiée, telle que les adresses avec le même préfixe de lien local ou de site local.</span><span class="sxs-lookup"><span data-stu-id="58e34-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="58e34-135">Cette option permet aux applications de placer des restrictions d’accès sur les sockets IPv6.</span><span class="sxs-lookup"><span data-stu-id="58e34-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="58e34-136">Ces restrictions permettent à une application qui s'exécute sur un réseau local privé de se renforcer facilement et efficacement contre les attaques externes.</span><span class="sxs-lookup"><span data-stu-id="58e34-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="58e34-137">Cette option élargit ou limite la portée d’un socket d’écoute, en permettant l’accès illimité des utilisateurs publics et privés, le cas échéant, ou en restreignant uniquement l’accès au même site, selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="58e34-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="58e34-138">Ce paramètre d’attribut `ipProtectionLevel` affecte uniquement le trafic entrant initial :</span><span class="sxs-lookup"><span data-stu-id="58e34-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="58e34-139">Un serveur TCP qui écoute les connexions entrantes sur un Socket.</span><span class="sxs-lookup"><span data-stu-id="58e34-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="58e34-140">Application UDP recevant un paquet sur un Socket.</span><span class="sxs-lookup"><span data-stu-id="58e34-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="58e34-141">Ce paramètre de configuration n’affecte pas les connexions TCP déjà établies (le trafic n’est pas restreint dans les deux sens) et n’affecte pas une application qui envoie des paquets UDP.</span><span class="sxs-lookup"><span data-stu-id="58e34-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="58e34-142">Les valeurs possibles pour le paramètre d’attribut `ipProtectionLevel` correspondent aux niveaux de protection définis dans l’énumération <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> comme suit :</span><span class="sxs-lookup"><span data-stu-id="58e34-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="58e34-143">**Valeur de l’attribut**</span><span class="sxs-lookup"><span data-stu-id="58e34-143">**Attribute Value**</span></span>|<span data-ttu-id="58e34-144">**Description**</span><span class="sxs-lookup"><span data-stu-id="58e34-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="58e34-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="58e34-145">EdgeRestricted</span></span>|<span data-ttu-id="58e34-146">Le niveau de protection IP est limité à l’arête.</span><span class="sxs-lookup"><span data-stu-id="58e34-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="58e34-147">Cette valeur est utilisée par les applications conçues pour fonctionner sur Internet.</span><span class="sxs-lookup"><span data-stu-id="58e34-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="58e34-148">Ce paramètre n’autorise pas la traversée de traduction d’adresses réseau (NAT) à l’aide de l’implémentation Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="58e34-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="58e34-149">Ces applications peuvent contourner les pare-feu IPv4, de sorte que les applications doivent être renforcées contre les attaques Internet dirigées vers le port ouvert.</span><span class="sxs-lookup"><span data-stu-id="58e34-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="58e34-150">Sur Windows Server 2003 et Windows XP, la valeur par défaut du niveau de protection IP sur un socket est limitée à la périphérie.</span><span class="sxs-lookup"><span data-stu-id="58e34-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="58e34-151">Sensible</span><span class="sxs-lookup"><span data-stu-id="58e34-151">Restricted</span></span>|<span data-ttu-id="58e34-152">Le niveau de protection IP est limité.</span><span class="sxs-lookup"><span data-stu-id="58e34-152">The IP protection level is restricted.</span></span> <span data-ttu-id="58e34-153">Cette valeur est utilisée par les applications intranet qui n’implémentent pas de scénarios Internet.</span><span class="sxs-lookup"><span data-stu-id="58e34-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="58e34-154">Ces applications ne sont généralement pas testées ou renforcées contre les attaques de type Internet.</span><span class="sxs-lookup"><span data-stu-id="58e34-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="58e34-155">Ce paramètre limite le trafic reçu à la liaison locale uniquement.</span><span class="sxs-lookup"><span data-stu-id="58e34-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="58e34-156">Non restreint</span><span class="sxs-lookup"><span data-stu-id="58e34-156">Unrestricted</span></span>|<span data-ttu-id="58e34-157">Le niveau de protection IP est illimité.</span><span class="sxs-lookup"><span data-stu-id="58e34-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="58e34-158">Cette valeur est utilisée par les applications conçues pour fonctionner sur Internet, y compris les applications tirant parti des fonctionnalités de traversée NAT IPv6 intégrées à Windows (Teredo, par exemple).</span><span class="sxs-lookup"><span data-stu-id="58e34-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="58e34-159">Ces applications peuvent contourner les pare-feu IPv4, de sorte que les applications doivent être renforcées contre les attaques Internet dirigées vers le port ouvert.</span><span class="sxs-lookup"><span data-stu-id="58e34-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="58e34-160">Sur Windows Server 2008 R2 et Windows Vista, la valeur par défaut du niveau de protection IP sur un socket est illimitée.</span><span class="sxs-lookup"><span data-stu-id="58e34-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="58e34-161">Non spécifié</span><span class="sxs-lookup"><span data-stu-id="58e34-161">Unspecified</span></span>|<span data-ttu-id="58e34-162">Le niveau de protection IP n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="58e34-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="58e34-163">Sur Windows 7 et Windows Server 2008 R2, la valeur par défaut du niveau de protection IP sur un socket n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="58e34-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="58e34-164">La valeur par défaut de l’attribut `ipProtectionLevel` n’est pas **spécifiée**.</span><span class="sxs-lookup"><span data-stu-id="58e34-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="58e34-165">La propriété <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> peut être utilisée pour récupérer la valeur actuelle de l’attribut `ipProtectionLevel` à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="58e34-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="58e34-166">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="58e34-166">Configuration Files</span></span>  
 <span data-ttu-id="58e34-167">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="58e34-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58e34-168">Exemple</span><span class="sxs-lookup"><span data-stu-id="58e34-168">Example</span></span>  
 <span data-ttu-id="58e34-169">L’exemple suivant montre comment spécifier que les ports de terminaison doivent être utilisés et que la <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> par défaut doit être illimitée.</span><span class="sxs-lookup"><span data-stu-id="58e34-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58e34-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58e34-170">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="58e34-171">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="58e34-171">Network Settings Schema</span></span>](index.md)
