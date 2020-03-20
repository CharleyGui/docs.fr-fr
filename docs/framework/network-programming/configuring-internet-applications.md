---
title: Configuration des applications Internet
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: ee4dc87383153ae4e8df0a3bed7cce5220e65405
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048629"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="30f32-102">Configuration des applications Internet</span><span class="sxs-lookup"><span data-stu-id="30f32-102">Configuring Internet Applications</span></span>
<span data-ttu-id="30f32-103">L [ \<system.Net’élément de configuration>> (Paramètres réseau)](../configure-apps/file-schema/network/system-net-element-network-settings.md) contient des informations de configuration réseau pour les applications.</span><span class="sxs-lookup"><span data-stu-id="30f32-103">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="30f32-104">À l’aide [ \<de l’élément system.Net> Element (Paramètres réseau),](../configure-apps/file-schema/network/system-net-element-network-settings.md) vous pouvez définir des serveurs proxy, définir les paramètres de gestion de connexion et inclure des modules d’authentification et de demande personnalisés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="30f32-104">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="30f32-105">[ \<L’élément par défautProxy> Element (Paramètres réseau)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) définit `GlobalProxySelection` le serveur proxy retourné par la classe.</span><span class="sxs-lookup"><span data-stu-id="30f32-105">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="30f32-106">Tout <xref:System.Net.HttpWebRequest> dont la propre propriété <xref:System.Net.HttpWebRequest.Proxy%2A> n’a pas une valeur spécifique utilise le proxy par défaut.</span><span class="sxs-lookup"><span data-stu-id="30f32-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="30f32-107">En plus de définir l’adresse du proxy, vous pouvez créer une liste d’adresses de serveurs qui n’utiliseront pas le serveur proxy, et vous pouvez indiquer que le proxy ne doit pas être utilisé pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="30f32-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="30f32-108">Il est important de noter que les paramètres de Microsoft Internet Explorer sont combinés avec les paramètres de configuration, ces derniers étant prioritaires.</span><span class="sxs-lookup"><span data-stu-id="30f32-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="30f32-109">L’exemple suivant définit `http://proxyserver` comme adresse du serveur proxy par défaut, indique que le proxy ne doit pas être utilisé pour les adresses locales, et spécifie que toutes les requêtes aux serveurs situés dans le domaine contoso.com doivent ignorer le proxy.</span><span class="sxs-lookup"><span data-stu-id="30f32-109">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="30f32-110">Utilisez [ \<l’élément de connexion> Element (Paramètres réseau)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) pour configurer le nombre de connexions persistantes qui peuvent être faites à un serveur spécifique ou à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="30f32-110">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="30f32-111">L’exemple suivant configure l’application pour qu’elle utilise deux connexions persistantes au serveur `www.contoso.com`, quatre connexions persistantes au serveur avec l’adresse IP 192.168.1.2, et une connexion persistante à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="30f32-111">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="30f32-112">Les modules d’authentification personnalisés sont configurés avec [ \<l’authentificationModules> Element (Network Settings).](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="30f32-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="30f32-113">Ils doivent implémenter l’interface <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="30f32-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="30f32-114">L’exemple suivant configure un module d’authentification personnalisé.</span><span class="sxs-lookup"><span data-stu-id="30f32-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="30f32-115">Vous pouvez utiliser l’élément [ \<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) pour configurer votre application pour utiliser des modules spécifiques au protocole personnalisé pour demander des informations à partir de ressources Internet.</span><span class="sxs-lookup"><span data-stu-id="30f32-115">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="30f32-116">Les modules spécifiés doivent implémenter l’interface <xref:System.Net.IWebRequestCreate>.</span><span class="sxs-lookup"><span data-stu-id="30f32-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="30f32-117">Vous pouvez substituer les modules HTTP, HTTPS et de requête de fichier par défaut en spécifiant votre module personnalisé dans le fichier de configuration, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="30f32-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30f32-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30f32-118">See also</span></span>

- [<span data-ttu-id="30f32-119">Programmation réseau dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="30f32-119">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="30f32-120">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="30f32-120">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="30f32-121">\<system.Net> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="30f32-121">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
