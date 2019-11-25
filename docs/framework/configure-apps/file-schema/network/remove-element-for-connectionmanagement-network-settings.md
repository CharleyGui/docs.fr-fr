---
title: <remove>, élément de connectionManagement (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 287e36dce65be7a002499d2cd22481018a1f4742
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089166"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="04968-102">\<supprimer > élément pour connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="04968-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="04968-103">Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="04968-103">Removes an IP address or DNS name from the connection management list.</span></span>  

<span data-ttu-id="04968-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="04968-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="04968-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="04968-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="04968-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement**](connectionmanagement-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="04968-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="04968-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**supprimer >**</span><span class="sxs-lookup"><span data-stu-id="04968-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="04968-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04968-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04968-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="04968-109">Attributes and Elements</span></span>  
 <span data-ttu-id="04968-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="04968-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04968-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="04968-111">Attributes</span></span>  
  
|<span data-ttu-id="04968-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="04968-112">**Attribute**</span></span>|<span data-ttu-id="04968-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="04968-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="04968-114">Une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="04968-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04968-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="04968-115">Child Elements</span></span>  
 <span data-ttu-id="04968-116">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="04968-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04968-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="04968-117">Parent Elements</span></span>  
  
|<span data-ttu-id="04968-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="04968-118">**Element**</span></span>|<span data-ttu-id="04968-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="04968-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="04968-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="04968-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="04968-121">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="04968-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04968-122">Notes</span><span class="sxs-lookup"><span data-stu-id="04968-122">Remarks</span></span>  
 <span data-ttu-id="04968-123">L’élément `remove` supprime l’entrée de la liste de gestion des connexions pour le serveur spécifié.</span><span class="sxs-lookup"><span data-stu-id="04968-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="04968-124">La valeur de l’attribut `address` doit être une adresse IP ou un nom d’hôte valide.</span><span class="sxs-lookup"><span data-stu-id="04968-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="04968-125">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="04968-125">Configuration Files</span></span>  
 <span data-ttu-id="04968-126">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="04968-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04968-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="04968-127">Example</span></span>  
 <span data-ttu-id="04968-128">L’exemple suivant supprime toutes les entrées de liste de gestion des connexions pour le `www.adventure-works.com` serveur, puis configure une application pour qu’elle utilise quatre connexions au serveur `www.contoso.com` et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="04968-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04968-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04968-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="04968-130">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="04968-130">Network Settings Schema</span></span>](index.md)
