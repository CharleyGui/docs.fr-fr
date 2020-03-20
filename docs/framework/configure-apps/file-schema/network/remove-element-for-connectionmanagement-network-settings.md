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
ms.openlocfilehash: 39ce85c3c15a2d4bdfce801a35e9ca088bd5091b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154736"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="e545a-102">\<supprimer> Element pour la connexionManagement (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="e545a-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="e545a-103">Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="e545a-103">Removes an IP address or DNS name from the connection management list.</span></span>  

<span data-ttu-id="e545a-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e545a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e545a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e545a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e545a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connexionManagement>**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e545a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="e545a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supprimer>**</span><span class="sxs-lookup"><span data-stu-id="e545a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e545a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e545a-108">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e545a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e545a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e545a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e545a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e545a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e545a-111">Attributes</span></span>  
  
|<span data-ttu-id="e545a-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="e545a-112">**Attribute**</span></span>|<span data-ttu-id="e545a-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="e545a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="e545a-114">Une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="e545a-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e545a-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e545a-115">Child Elements</span></span>  
 <span data-ttu-id="e545a-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e545a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e545a-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e545a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e545a-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="e545a-118">**Element**</span></span>|<span data-ttu-id="e545a-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="e545a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e545a-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e545a-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="e545a-121">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="e545a-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e545a-122">Notes </span><span class="sxs-lookup"><span data-stu-id="e545a-122">Remarks</span></span>  
 <span data-ttu-id="e545a-123">L’élément `remove` supprime l’entrée de la liste de gestion de connexion pour le serveur spécifié.</span><span class="sxs-lookup"><span data-stu-id="e545a-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="e545a-124">La valeur `address` de l’attribut doit être une adresse IP valide ou un nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="e545a-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e545a-125">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="e545a-125">Configuration Files</span></span>  
 <span data-ttu-id="e545a-126">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e545a-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e545a-127"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e545a-127">Example</span></span>  
 <span data-ttu-id="e545a-128">L’exemple suivant supprime toutes les entrées `www.adventure-works.com` de liste de gestion de connexion `www.contoso.com` pour le serveur, puis configure une application pour utiliser quatre connexions au serveur et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="e545a-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e545a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e545a-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="e545a-130">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="e545a-130">Network Settings Schema</span></span>](index.md)
