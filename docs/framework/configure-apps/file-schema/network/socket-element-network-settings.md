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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089088"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="2bce5-102">\<socket>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="2bce5-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="2bce5-103">Spécifie si les opérations de socket utilisent des ports de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2bce5-103">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="2bce5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bce5-104">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bce5-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2bce5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2bce5-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2bce5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bce5-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="2bce5-107">Attributes</span></span>  
  
|<span data-ttu-id="2bce5-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="2bce5-108">**Attribute**</span></span>|<span data-ttu-id="2bce5-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="2bce5-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="2bce5-110">Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode Accept.</span><span class="sxs-lookup"><span data-stu-id="2bce5-110">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="2bce5-111">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="2bce5-111">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="2bce5-112">Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode Connect.</span><span class="sxs-lookup"><span data-stu-id="2bce5-112">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="2bce5-113">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="2bce5-113">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="2bce5-114">Spécifie la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> à utiliser pour un Socket.</span><span class="sxs-lookup"><span data-stu-id="2bce5-114">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="2bce5-115">La valeur par défaut dépend de la version de Windows.</span><span class="sxs-lookup"><span data-stu-id="2bce5-115">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bce5-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2bce5-116">Child Elements</span></span>  
 <span data-ttu-id="2bce5-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2bce5-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2bce5-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2bce5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2bce5-119">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="2bce5-119">**Element**</span></span>|<span data-ttu-id="2bce5-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="2bce5-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2bce5-121">settings</span><span class="sxs-lookup"><span data-stu-id="2bce5-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="2bce5-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="2bce5-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bce5-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="2bce5-123">Remarks</span></span>  
 <span data-ttu-id="2bce5-124">Les `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` attributs et sont utilisés pour spécifier le comportement par défaut en ce qui concerne l’utilisation des ports de terminaison par les classes dans l' <xref:System.Net.Sockets?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2bce5-124">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="2bce5-125">Les ports de terminaison sont recommandés pour les applications serveur hautes performances.</span><span class="sxs-lookup"><span data-stu-id="2bce5-125">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="2bce5-126">La valeur par défaut pour `alwaysUseCompletionPortsForAccept` les `alwaysUseCompletionPortsForConnect` attributs et est **false**.</span><span class="sxs-lookup"><span data-stu-id="2bce5-126">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="2bce5-127">Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> peut être utilisé pour récupérer la valeur actuelle de l' `alwaysUseCompletionPortsForAccept` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2bce5-127">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="2bce5-128">Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> peut être utilisé pour récupérer la valeur actuelle de l' `alwaysUseCompletionPortsForConnect` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2bce5-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2bce5-129">L' `ipProtectionLevel` attribut spécifie la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> à utiliser pour un Socket.</span><span class="sxs-lookup"><span data-stu-id="2bce5-129">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="2bce5-130">La <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriété permet la configuration d’une restriction pour un socket IPv6 vers une étendue spécifiée, telle que les adresses avec le même préfixe de lien local ou de site local.</span><span class="sxs-lookup"><span data-stu-id="2bce5-130">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="2bce5-131">Cette option permet aux applications de placer des restrictions d’accès sur les sockets IPv6.</span><span class="sxs-lookup"><span data-stu-id="2bce5-131">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="2bce5-132">Ces restrictions permettent à une application qui s'exécute sur un réseau local privé de se renforcer facilement et efficacement contre les attaques externes.</span><span class="sxs-lookup"><span data-stu-id="2bce5-132">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="2bce5-133">Cette option élargit ou limite la portée d’un socket d’écoute, en permettant l’accès illimité des utilisateurs publics et privés, le cas échéant, ou en restreignant uniquement l’accès au même site, selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="2bce5-133">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="2bce5-134">Ce `ipProtectionLevel` paramètre d’attribut affecte uniquement le trafic entrant initial :</span><span class="sxs-lookup"><span data-stu-id="2bce5-134">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="2bce5-135">Un serveur TCP qui écoute les connexions entrantes sur un Socket.</span><span class="sxs-lookup"><span data-stu-id="2bce5-135">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="2bce5-136">Application UDP recevant un paquet sur un Socket.</span><span class="sxs-lookup"><span data-stu-id="2bce5-136">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="2bce5-137">Ce paramètre de configuration n’affecte pas les connexions TCP déjà établies (le trafic n’est pas restreint dans les deux sens) et n’affecte pas une application qui envoie des paquets UDP.</span><span class="sxs-lookup"><span data-stu-id="2bce5-137">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="2bce5-138">Les valeurs possibles pour le `ipProtectionLevel` paramètre d’attribut correspondent aux niveaux de protection définis spécifiés dans l' <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> énumération comme suit :</span><span class="sxs-lookup"><span data-stu-id="2bce5-138">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="2bce5-139">**Valeur d'attribut**</span><span class="sxs-lookup"><span data-stu-id="2bce5-139">**Attribute Value**</span></span>|<span data-ttu-id="2bce5-140">**Description**</span><span class="sxs-lookup"><span data-stu-id="2bce5-140">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="2bce5-141">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="2bce5-141">EdgeRestricted</span></span>|<span data-ttu-id="2bce5-142">Le niveau de protection IP est limité à un périmètre donné.</span><span class="sxs-lookup"><span data-stu-id="2bce5-142">The IP protection level is edge restricted.</span></span> <span data-ttu-id="2bce5-143">Cette valeur peut être utilisée par les applications conçues pour fonctionner sur Internet.</span><span class="sxs-lookup"><span data-stu-id="2bce5-143">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="2bce5-144">Ce paramètre n'autorise pas la traversée du traducteur d'adresses réseau (NAT) à l'aide de l'implémentation de Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="2bce5-144">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="2bce5-145">Ces applications peuvent contourner les pare-feux IPv4 ; elles doivent donc être renforcées contre les attaques Internet dirigées sur le port ouvert.</span><span class="sxs-lookup"><span data-stu-id="2bce5-145">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="2bce5-146">Sous Windows Server 2003 et Windows XP, la valeur par défaut pour le niveau de protection IP sur un socket est Périmètre limité.</span><span class="sxs-lookup"><span data-stu-id="2bce5-146">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="2bce5-147">Restreint</span><span class="sxs-lookup"><span data-stu-id="2bce5-147">Restricted</span></span>|<span data-ttu-id="2bce5-148">Le niveau de protection IP est limité.</span><span class="sxs-lookup"><span data-stu-id="2bce5-148">The IP protection level is restricted.</span></span> <span data-ttu-id="2bce5-149">Cette valeur peut être utilisée par les applications intranet qui n'implémentent pas de scénarios Internet.</span><span class="sxs-lookup"><span data-stu-id="2bce5-149">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="2bce5-150">Ces applications ne sont généralement pas testées ou renforcées contre les attaques Internet.</span><span class="sxs-lookup"><span data-stu-id="2bce5-150">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="2bce5-151">Ce paramètre limitera uniquement le trafic reçu aux liens locaux.</span><span class="sxs-lookup"><span data-stu-id="2bce5-151">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="2bce5-152">Non restreint</span><span class="sxs-lookup"><span data-stu-id="2bce5-152">Unrestricted</span></span>|<span data-ttu-id="2bce5-153">Le niveau de protection IP est illimité.</span><span class="sxs-lookup"><span data-stu-id="2bce5-153">The IP protection level is unrestricted.</span></span> <span data-ttu-id="2bce5-154">Cette valeur peut être utilisée par les applications conçues pour fonctionner sur Internet, notamment les applications qui tirent parti des fonctions de traversée NAT IPv6 intégrées à Windows (Teredo, par exemple).</span><span class="sxs-lookup"><span data-stu-id="2bce5-154">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="2bce5-155">Ces applications peuvent contourner les pare-feux IPv4 ; elles doivent donc être renforcées contre les attaques Internet dirigées sur le port ouvert.</span><span class="sxs-lookup"><span data-stu-id="2bce5-155">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="2bce5-156">Sous Windows Server 2008 R2 et Windows Vista, la valeur par défaut pour le niveau de protection IP sur un socket est illimitée.</span><span class="sxs-lookup"><span data-stu-id="2bce5-156">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="2bce5-157">Non spécifié</span><span class="sxs-lookup"><span data-stu-id="2bce5-157">Unspecified</span></span>|<span data-ttu-id="2bce5-158">Le niveau de protection IP n'est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="2bce5-158">The IP protection level is unspecified.</span></span> <span data-ttu-id="2bce5-159">Sous Windows 7 et Windows Server 2008 R2, la valeur par défaut pour le niveau de protection IP sur un socket n'est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2bce5-159">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="2bce5-160">La valeur par défaut de l' `ipProtectionLevel` attribut n’est pas **spécifiée**.</span><span class="sxs-lookup"><span data-stu-id="2bce5-160">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="2bce5-161">La <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriété peut être utilisée pour récupérer la valeur actuelle de l' `ipProtectionLevel` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2bce5-161">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2bce5-162">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="2bce5-162">Configuration Files</span></span>  
 <span data-ttu-id="2bce5-163">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2bce5-163">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bce5-164">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bce5-164">Example</span></span>  
 <span data-ttu-id="2bce5-165">L’exemple suivant montre comment spécifier que les ports de terminaison doivent être utilisés et que la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> doit être illimitée.</span><span class="sxs-lookup"><span data-stu-id="2bce5-165">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2bce5-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bce5-166">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="2bce5-167">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="2bce5-167">Network Settings Schema</span></span>](index.md)
