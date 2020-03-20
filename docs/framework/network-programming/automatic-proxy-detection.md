---
title: Détection automatique de proxy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
ms.openlocfilehash: 4c5bc9e0efb39032d388d141e8bccf3e520ebd45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180900"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="0d657-102">Détection automatique de proxy</span><span class="sxs-lookup"><span data-stu-id="0d657-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="0d657-103">La détection automatique de proxy est un processus par lequel un serveur proxy web est identifié par le système et utilisé pour envoyer des demandes pour le compte du client.</span><span class="sxs-lookup"><span data-stu-id="0d657-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="0d657-104">Cette fonctionnalité est également connue sous le nom de Découverte automatique de proxy Web (WPAD, Web Proxy Auto-Discovery).</span><span class="sxs-lookup"><span data-stu-id="0d657-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="0d657-105">Quand la détection automatique de proxy est activée, le système tente de localiser un script de configuration de proxy qui est chargé de retourner l’ensemble des proxys pouvant être utilisés pour la requête.</span><span class="sxs-lookup"><span data-stu-id="0d657-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="0d657-106">Si le script de configuration de proxy est trouvé, il est téléchargé, compilé et exécuté sur l’ordinateur local quand les informations de proxy, le flux de requête ou la réponse sont obtenus pour une requête qui utilise une instance de <xref:System.Net.WebProxy>.</span><span class="sxs-lookup"><span data-stu-id="0d657-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="0d657-107">La détection automatique de proxy est effectuée par la classe <xref:System.Net.WebProxy> et peut utiliser des paramètres au niveau de la requête, des paramètres dans des fichiers de configuration et des paramètres spécifiés à l’aide de la boîte de dialogue **Réseau local** d’Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0d657-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d657-108">Vous pouvez afficher la boîte de dialogue **Réseau local** d’Internet Explorer en sélectionnant **Outils** dans le menu principal d’Internet Explorer, puis **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="0d657-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="0d657-109">Ensuite, sélectionnez l’onglet **Connexions** et cliquez sur **Paramètres du réseau local**.</span><span class="sxs-lookup"><span data-stu-id="0d657-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="0d657-110">Quand la détection automatique de proxy est activée, la classe <xref:System.Net.WebProxy> tente de localiser le script de configuration de proxy comme suit :</span><span class="sxs-lookup"><span data-stu-id="0d657-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1. <span data-ttu-id="0d657-111">La fonction `InternetQueryOption` WinINet est utilisée pour accéder au script de configuration de proxy le plus récemment détecté par Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0d657-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2. <span data-ttu-id="0d657-112">Si le script est introuvable, la classe <xref:System.Net.WebProxy> utilise le protocole DHCP (Dynamic Host Configuration Protocol) pour accéder au script.</span><span class="sxs-lookup"><span data-stu-id="0d657-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="0d657-113">Le serveur DHCP peut répondre avec l’emplacement (nom d’hôte) du script ou avec l’URL complète du script.</span><span class="sxs-lookup"><span data-stu-id="0d657-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3. <span data-ttu-id="0d657-114">Si le protocole DHCP n’identifie pas l’hôte WPAD, le système DNS est interrogé pour trouver un hôte avec WPAD comme nom ou alias.</span><span class="sxs-lookup"><span data-stu-id="0d657-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4. <span data-ttu-id="0d657-115">Si l’hôte n’est pas identifié et que l’emplacement d’un script de configuration de proxy est spécifié par les paramètres de réseau local d’Internet Explorer ou un fichier de configuration, cet emplacement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0d657-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d657-116">Les applications qui s’exécutent en tant que service NT ou dans le cadre d’ASP.NET utilisent les paramètres de serveur proxy d’Internet Explorer (s’ils sont disponibles) de l’utilisateur appelant.</span><span class="sxs-lookup"><span data-stu-id="0d657-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="0d657-117">Ces paramètres peuvent ne pas être disponibles pour toutes les applications de service.</span><span class="sxs-lookup"><span data-stu-id="0d657-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="0d657-118">Les proxys sont configurés sur la base de chaque connectoid.</span><span class="sxs-lookup"><span data-stu-id="0d657-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="0d657-119">Un connectoid est un élément dans la boîte de dialogue de connexion réseau. Il peut s’agir d’un appareil réseau physique (un modem ou une carte Ethernet) ou d’une interface virtuelle (par exemple, une connexion VPN qui s’exécute sur un appareil réseau).</span><span class="sxs-lookup"><span data-stu-id="0d657-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="0d657-120">Quand un connectoid change (par exemple quand une connexion sans fil change un point d’accès, ou qu’un réseau VPN est activé), l’algorithme de détection de proxy est réexécuté.</span><span class="sxs-lookup"><span data-stu-id="0d657-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="0d657-121">Par défaut, les paramètres de proxy d’Internet Explorer sont utilisés pour détecter le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="0d657-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="0d657-122">Si votre application s’exécute sous un compte non interactif (sans moyen pratique de configurer les paramètres de proxy IE), ou si vous [ \<](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) souhaitez utiliser des paramètres proxy différents des paramètres IE, vous pouvez configurer votre proxy en créant un fichier de configuration avec les éléments de> Element (Paramètres réseau) et [ \<proxy> Element (Paramètres réseau)](../configure-apps/file-schema/network/proxy-element-network-settings.md) définis.</span><span class="sxs-lookup"><span data-stu-id="0d657-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="0d657-123">Pour les requêtes que vous créez, vous pouvez désactiver la détection automatique de proxy au niveau de la requête en utilisant un <xref:System.Net.WebRequest.Proxy%2A> null avec votre requête, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="0d657-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub
```  
  
 <span data-ttu-id="0d657-124">Les requêtes qui n’ont pas de proxy utilisent le proxy par défaut de votre domaine d’application, qui est disponible dans la propriété <xref:System.Net.WebRequest.DefaultWebProxy%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d657-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d657-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d657-125">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="0d657-126">\<system.Net> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="0d657-126">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
