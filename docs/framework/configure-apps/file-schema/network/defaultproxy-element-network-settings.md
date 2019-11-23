---
title: <defaultProxy>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 0945629c1395917bc1cf825f2ba84d20afa99957
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698207"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="adaa1-102">\<defaultProxy >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="adaa1-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="adaa1-103">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="adaa1-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[<span data-ttu-id="adaa1-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="adaa1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="adaa1-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="adaa1-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="adaa1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultProxy** ></span><span class="sxs-lookup"><span data-stu-id="adaa1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adaa1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adaa1-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adaa1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="adaa1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="adaa1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="adaa1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adaa1-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="adaa1-110">Attributes</span></span>  
  
|<span data-ttu-id="adaa1-111">**Élément**</span><span class="sxs-lookup"><span data-stu-id="adaa1-111">**Element**</span></span>|<span data-ttu-id="adaa1-112">**Description**</span><span class="sxs-lookup"><span data-stu-id="adaa1-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="adaa1-113">Spécifie si un proxy web est utilisé.</span><span class="sxs-lookup"><span data-stu-id="adaa1-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="adaa1-114">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="adaa1-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="adaa1-115">Spécifie si les informations d'identification par défaut associées à cet hôte sont utilisées pour accéder au proxy web.</span><span class="sxs-lookup"><span data-stu-id="adaa1-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="adaa1-116">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="adaa1-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adaa1-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="adaa1-117">Child Elements</span></span>  
  
|<span data-ttu-id="adaa1-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="adaa1-118">**Element**</span></span>|<span data-ttu-id="adaa1-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="adaa1-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="adaa1-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="adaa1-120">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="adaa1-121">Fournit un ensemble d'expressions régulières décrivant les adresses qui n'utilisent pas le proxy.</span><span class="sxs-lookup"><span data-stu-id="adaa1-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="adaa1-122">module</span><span class="sxs-lookup"><span data-stu-id="adaa1-122">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="adaa1-123">Ajoute un nouveau module proxy à l'application.</span><span class="sxs-lookup"><span data-stu-id="adaa1-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="adaa1-124">proxy</span><span class="sxs-lookup"><span data-stu-id="adaa1-124">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="adaa1-125">Définit un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="adaa1-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adaa1-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="adaa1-126">Parent Elements</span></span>  
  
|<span data-ttu-id="adaa1-127">**Élément**</span><span class="sxs-lookup"><span data-stu-id="adaa1-127">**Element**</span></span>|<span data-ttu-id="adaa1-128">**Description**</span><span class="sxs-lookup"><span data-stu-id="adaa1-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="adaa1-129">system.net</span><span class="sxs-lookup"><span data-stu-id="adaa1-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="adaa1-130">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="adaa1-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adaa1-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="adaa1-131">Remarks</span></span>  
 <span data-ttu-id="adaa1-132">Si l'élément defaultProxy est vide, les paramètres du proxy Internet Explorer sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="adaa1-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="adaa1-133">Ce comportement est différent de la version 1.1 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="adaa1-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="adaa1-134">Une exception est levée si l’élément de [module](module-element-network-settings.md) spécifie un type non public, si le type ne dérive pas de la classe <xref:System.Net.IWebProxy>, une exception du constructeur sans paramètre de cet objet s’est produite, ou une exception s’est produite lors de la récupération du proxy par défaut spécifié par le système.</span><span class="sxs-lookup"><span data-stu-id="adaa1-134">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="adaa1-135">La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="adaa1-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="adaa1-136">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="adaa1-136">Configuration Files</span></span>  
 <span data-ttu-id="adaa1-137">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="adaa1-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="adaa1-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="adaa1-138">Example</span></span>  
 <span data-ttu-id="adaa1-139">L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local et contoso.com.</span><span class="sxs-lookup"><span data-stu-id="adaa1-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adaa1-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adaa1-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="adaa1-141">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="adaa1-141">Network Settings Schema</span></span>](index.md)
