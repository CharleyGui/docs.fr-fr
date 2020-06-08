---
title: <defaultProxy>, élément (paramètres réseau)
description: L' <defaultProxy> élément paramètres réseau configure le serveur proxy http (Hypertext Transfer Protocol) dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 915fdc96dbd4d417f9c9e6aa3ff96de3026491ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504600"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="6540c-103">\<defaultProxy>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6540c-103">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="6540c-104">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="6540c-104">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="6540c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6540c-105">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6540c-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6540c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6540c-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6540c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6540c-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="6540c-108">Attributes</span></span>  
  
|<span data-ttu-id="6540c-109">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="6540c-109">**Element**</span></span>|<span data-ttu-id="6540c-110">**Description**</span><span class="sxs-lookup"><span data-stu-id="6540c-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="6540c-111">Spécifie si un proxy web est utilisé.</span><span class="sxs-lookup"><span data-stu-id="6540c-111">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="6540c-112">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="6540c-112">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="6540c-113">Spécifie si les informations d'identification par défaut associées à cet hôte sont utilisées pour accéder au proxy web.</span><span class="sxs-lookup"><span data-stu-id="6540c-113">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="6540c-114">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="6540c-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6540c-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6540c-115">Child Elements</span></span>  
  
|<span data-ttu-id="6540c-116">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="6540c-116">**Element**</span></span>|<span data-ttu-id="6540c-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="6540c-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6540c-118">BypassList</span><span class="sxs-lookup"><span data-stu-id="6540c-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="6540c-119">Fournit un ensemble d'expressions régulières décrivant les adresses qui n'utilisent pas le proxy.</span><span class="sxs-lookup"><span data-stu-id="6540c-119">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="6540c-120">modules</span><span class="sxs-lookup"><span data-stu-id="6540c-120">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="6540c-121">Ajoute un nouveau module proxy à l'application.</span><span class="sxs-lookup"><span data-stu-id="6540c-121">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="6540c-122">procur</span><span class="sxs-lookup"><span data-stu-id="6540c-122">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="6540c-123">Définit un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="6540c-123">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6540c-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6540c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6540c-125">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="6540c-125">**Element**</span></span>|<span data-ttu-id="6540c-126">**Description**</span><span class="sxs-lookup"><span data-stu-id="6540c-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6540c-127">system.net</span><span class="sxs-lookup"><span data-stu-id="6540c-127">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="6540c-128">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="6540c-128">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6540c-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="6540c-129">Remarks</span></span>  
 <span data-ttu-id="6540c-130">Si l'élément defaultProxy est vide, les paramètres du proxy Internet Explorer sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="6540c-130">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="6540c-131">Ce comportement est différent de la version 1.1 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6540c-131">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="6540c-132">Une exception est levée si l’élément de [module](module-element-network-settings.md) spécifie un type non public, si le type ne dérive pas de la <xref:System.Net.IWebProxy> classe, une exception du constructeur sans paramètre de cet objet s’est produite, ou une exception s’est produite lors de la récupération du proxy par défaut spécifié par le système.</span><span class="sxs-lookup"><span data-stu-id="6540c-132">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="6540c-133">La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="6540c-133">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6540c-134">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6540c-134">Configuration Files</span></span>  
 <span data-ttu-id="6540c-135">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6540c-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6540c-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="6540c-136">Example</span></span>  
 <span data-ttu-id="6540c-137">L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local et contoso.com.</span><span class="sxs-lookup"><span data-stu-id="6540c-137">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6540c-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6540c-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6540c-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="6540c-139">Network Settings Schema</span></span>](index.md)
