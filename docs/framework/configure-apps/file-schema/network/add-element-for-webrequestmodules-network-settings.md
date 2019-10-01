---
title: <add>, élément de webRequestModules (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 0248706ed78de160ef0131a0c7595374febf1aa9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699589"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="fd165-102">\<add > élément de webRequestModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="fd165-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="fd165-103">Ajoute un module de demande Web personnalisé à l’application.</span><span class="sxs-lookup"><span data-stu-id="fd165-103">Adds a custom Web request module to the application.</span></span>  
  
[<span data-ttu-id="fd165-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="fd165-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="fd165-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fd165-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="fd165-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fd165-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="fd165-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="fd165-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd165-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd165-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd165-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd165-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fd165-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fd165-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd165-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd165-111">Attributes</span></span>  
  
|<span data-ttu-id="fd165-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="fd165-112">**Attribute**</span></span>|<span data-ttu-id="fd165-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="fd165-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="fd165-114">Préfixe URI pour les requêtes gérées par ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="fd165-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="fd165-115">Le nom de type qualifié complet (indiqué par la propriété <xref:System.Type.FullName%2A>) et le nom de l’assembly (indiqué par la propriété <xref:System.Reflection.Assembly.FullName%2A>), séparés par une virgule, qui implémente ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="fd165-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd165-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd165-116">Child Elements</span></span>  
 <span data-ttu-id="fd165-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd165-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd165-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd165-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fd165-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="fd165-119">**Element**</span></span>|<span data-ttu-id="fd165-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="fd165-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fd165-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="fd165-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="fd165-122">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="fd165-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd165-123">Notes</span><span class="sxs-lookup"><span data-stu-id="fd165-123">Remarks</span></span>  
 <span data-ttu-id="fd165-124">L’attribut `prefix` définit le préfixe URI qui utilise le module de demande Web spécifié.</span><span class="sxs-lookup"><span data-stu-id="fd165-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="fd165-125">Les modules de demande Web sont généralement enregistrés pour gérer un protocole spécifique, tel que HTTP ou FTP, mais peuvent être inscrits pour gérer une demande à un serveur ou à un chemin d’accès spécifique sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="fd165-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="fd165-126">Le module de demande Web est créé lorsqu’un préfixe d’URI correspondant est passé à la méthode <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd165-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="fd165-127">La valeur de l’attribut `prefix` doit être celle des caractères de début d’un URI valide.</span><span class="sxs-lookup"><span data-stu-id="fd165-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="fd165-128">Par exemple, `http` ou `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="fd165-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="fd165-129">La valeur de l’attribut `type` doit être un nom de type valide et le nom d’assembly correspondant, séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="fd165-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="fd165-130">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="fd165-130">Configuration Files</span></span>  
 <span data-ttu-id="fd165-131">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="fd165-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd165-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd165-132">Example</span></span>  
 <span data-ttu-id="fd165-133">L’exemple suivant inscrit un module de demande Web personnalisé pour HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd165-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="fd165-134">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="fd165-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd165-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd165-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="fd165-136">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="fd165-136">Network Settings Schema</span></span>](index.md)
