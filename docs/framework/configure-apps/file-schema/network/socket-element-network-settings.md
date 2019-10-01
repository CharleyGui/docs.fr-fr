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
ms.openlocfilehash: ec2c8388411e24940041dc9dcb7f6a6755e89805
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697586"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="b1257-102">\<socket >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b1257-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="b1257-103">Spécifie si les opérations de socket utilisent des ports de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b1257-103">Specifies whether socket operations use completion ports.</span></span>  
  
[<span data-ttu-id="b1257-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="b1257-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b1257-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1257-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="b1257-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1257-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="b1257-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<socket >**</span><span class="sxs-lookup"><span data-stu-id="b1257-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1257-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1257-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1257-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b1257-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b1257-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b1257-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1257-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="b1257-111">Attributes</span></span>  
  
|<span data-ttu-id="b1257-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="b1257-112">**Attribute**</span></span>|<span data-ttu-id="b1257-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="b1257-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="b1257-114">Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode Accept.</span><span class="sxs-lookup"><span data-stu-id="b1257-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="b1257-115">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="b1257-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="b1257-116">Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode Connect.</span><span class="sxs-lookup"><span data-stu-id="b1257-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="b1257-117">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="b1257-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="b1257-118">Spécifie la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> à utiliser pour un Socket.</span><span class="sxs-lookup"><span data-stu-id="b1257-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="b1257-119">La valeur par défaut dépend de la version de Windows.</span><span class="sxs-lookup"><span data-stu-id="b1257-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1257-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b1257-120">Child Elements</span></span>  
 <span data-ttu-id="b1257-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b1257-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1257-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b1257-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b1257-123">**Élément**</span><span class="sxs-lookup"><span data-stu-id="b1257-123">**Element**</span></span>|<span data-ttu-id="b1257-124">**Description**</span><span class="sxs-lookup"><span data-stu-id="b1257-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1257-125">settings</span><span class="sxs-lookup"><span data-stu-id="b1257-125">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b1257-126">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="b1257-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1257-127">Notes</span><span class="sxs-lookup"><span data-stu-id="b1257-127">Remarks</span></span>  
 <span data-ttu-id="b1257-128">Les attributs `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` sont utilisés pour spécifier le comportement par défaut concernant l’utilisation des ports de terminaison par les classes de l’espace de noms <xref:System.Net.Sockets?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1257-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="b1257-129">Les ports de terminaison sont recommandés pour les applications serveur hautes performances.</span><span class="sxs-lookup"><span data-stu-id="b1257-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="b1257-130">La valeur par défaut pour les attributs `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` est **false**.</span><span class="sxs-lookup"><span data-stu-id="b1257-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="b1257-131">La <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> peut être utilisée pour récupérer la valeur actuelle de l’attribut `alwaysUseCompletionPortsForAccept` à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="b1257-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="b1257-132">La <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> peut être utilisée pour récupérer la valeur actuelle de l’attribut `alwaysUseCompletionPortsForConnect` à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="b1257-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="b1257-133">L’attribut `ipProtectionLevel` spécifie la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> à utiliser pour un Socket.</span><span class="sxs-lookup"><span data-stu-id="b1257-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="b1257-134">La propriété <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> active la configuration d’une restriction pour un socket IPv6 à une étendue spécifiée, telle que les adresses avec le même préfixe de lien local ou de site local.</span><span class="sxs-lookup"><span data-stu-id="b1257-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="b1257-135">Cette option permet aux applications de placer des restrictions d’accès sur les sockets IPv6.</span><span class="sxs-lookup"><span data-stu-id="b1257-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="b1257-136">Ces restrictions permettent à une application qui s'exécute sur un réseau local privé de se renforcer facilement et efficacement contre les attaques externes.</span><span class="sxs-lookup"><span data-stu-id="b1257-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="b1257-137">Cette option élargit ou limite la portée d’un socket d’écoute, en permettant l’accès illimité des utilisateurs publics et privés, le cas échéant, ou en restreignant uniquement l’accès au même site, selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="b1257-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="b1257-138">Ce paramètre d’attribut `ipProtectionLevel` affecte uniquement le trafic entrant initial :</span><span class="sxs-lookup"><span data-stu-id="b1257-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="b1257-139">Un serveur TCP qui écoute les connexions entrantes sur un Socket.</span><span class="sxs-lookup"><span data-stu-id="b1257-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="b1257-140">Application UDP recevant un paquet sur un Socket.</span><span class="sxs-lookup"><span data-stu-id="b1257-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="b1257-141">Ce paramètre de configuration n’affecte pas les connexions TCP déjà établies (le trafic n’est pas restreint dans les deux sens) et n’affecte pas une application qui envoie des paquets UDP.</span><span class="sxs-lookup"><span data-stu-id="b1257-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="b1257-142">Les valeurs possibles pour le paramètre d’attribut `ipProtectionLevel` correspondent aux niveaux de protection définis spécifiés dans l’énumération <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> comme suit :</span><span class="sxs-lookup"><span data-stu-id="b1257-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="b1257-143">**Valeur de l’attribut**</span><span class="sxs-lookup"><span data-stu-id="b1257-143">**Attribute Value**</span></span>|<span data-ttu-id="b1257-144">**Description**</span><span class="sxs-lookup"><span data-stu-id="b1257-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="b1257-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="b1257-145">EdgeRestricted</span></span>|<span data-ttu-id="b1257-146">Le niveau de protection IP est limité à l’arête.</span><span class="sxs-lookup"><span data-stu-id="b1257-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="b1257-147">Cette valeur est utilisée par les applications conçues pour fonctionner sur Internet.</span><span class="sxs-lookup"><span data-stu-id="b1257-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="b1257-148">Ce paramètre n’autorise pas la traversée de traduction d’adresses réseau (NAT) à l’aide de l’implémentation Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="b1257-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="b1257-149">Ces applications peuvent contourner les pare-feu IPv4, de sorte que les applications doivent être renforcées contre les attaques Internet dirigées vers le port ouvert.</span><span class="sxs-lookup"><span data-stu-id="b1257-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="b1257-150">Sur Windows Server 2003 et Windows XP, la valeur par défaut du niveau de protection IP sur un socket est limitée à la périphérie.</span><span class="sxs-lookup"><span data-stu-id="b1257-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="b1257-151">sensible</span><span class="sxs-lookup"><span data-stu-id="b1257-151">Restricted</span></span>|<span data-ttu-id="b1257-152">Le niveau de protection IP est limité.</span><span class="sxs-lookup"><span data-stu-id="b1257-152">The IP protection level is restricted.</span></span> <span data-ttu-id="b1257-153">Cette valeur est utilisée par les applications intranet qui n’implémentent pas de scénarios Internet.</span><span class="sxs-lookup"><span data-stu-id="b1257-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="b1257-154">Ces applications ne sont généralement pas testées ou renforcées contre les attaques de type Internet.</span><span class="sxs-lookup"><span data-stu-id="b1257-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="b1257-155">Ce paramètre limite le trafic reçu à la liaison locale uniquement.</span><span class="sxs-lookup"><span data-stu-id="b1257-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="b1257-156">Non restreint</span><span class="sxs-lookup"><span data-stu-id="b1257-156">Unrestricted</span></span>|<span data-ttu-id="b1257-157">Le niveau de protection IP est illimité.</span><span class="sxs-lookup"><span data-stu-id="b1257-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="b1257-158">Cette valeur est utilisée par les applications conçues pour fonctionner sur Internet, y compris les applications tirant parti des fonctionnalités de traversée NAT IPv6 intégrées à Windows (Teredo, par exemple).</span><span class="sxs-lookup"><span data-stu-id="b1257-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="b1257-159">Ces applications peuvent contourner les pare-feu IPv4, de sorte que les applications doivent être renforcées contre les attaques Internet dirigées vers le port ouvert.</span><span class="sxs-lookup"><span data-stu-id="b1257-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="b1257-160">Sur Windows Server 2008 R2 et Windows Vista, la valeur par défaut du niveau de protection IP sur un socket est illimitée.</span><span class="sxs-lookup"><span data-stu-id="b1257-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="b1257-161">Non spécifié</span><span class="sxs-lookup"><span data-stu-id="b1257-161">Unspecified</span></span>|<span data-ttu-id="b1257-162">Le niveau de protection IP n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1257-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="b1257-163">Sur Windows 7 et Windows Server 2008 R2, la valeur par défaut du niveau de protection IP sur un socket n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b1257-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="b1257-164">La valeur par défaut de l’attribut `ipProtectionLevel` n’est pas **spécifiée**.</span><span class="sxs-lookup"><span data-stu-id="b1257-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="b1257-165">La propriété <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> peut être utilisée pour récupérer la valeur actuelle de l’attribut `ipProtectionLevel` à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="b1257-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b1257-166">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b1257-166">Configuration Files</span></span>  
 <span data-ttu-id="b1257-167">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b1257-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1257-168">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1257-168">Example</span></span>  
 <span data-ttu-id="b1257-169">L’exemple suivant montre comment spécifier que les ports de terminaison doivent être utilisés et que la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> doit être illimitée.</span><span class="sxs-lookup"><span data-stu-id="b1257-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1257-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1257-170">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="b1257-171">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="b1257-171">Network Settings Schema</span></span>](index.md)
