---
title: <connectionManagement>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: d377a77a4a1b4c57e9edd4fbfa364387f1bae479
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699428"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="856a7-102">\<connectionManagement >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="856a7-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="856a7-103">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="856a7-103">Specifies the maximum number of connections to a network host.</span></span>  
  
[<span data-ttu-id="856a7-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="856a7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="856a7-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="856a7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="856a7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<connectionManagement >**</span><span class="sxs-lookup"><span data-stu-id="856a7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="856a7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="856a7-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="856a7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="856a7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="856a7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="856a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="856a7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="856a7-110">Attributes</span></span>  
 <span data-ttu-id="856a7-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="856a7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="856a7-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="856a7-112">Child Elements</span></span>  
  
|<span data-ttu-id="856a7-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="856a7-113">**Element**</span></span>|<span data-ttu-id="856a7-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="856a7-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="856a7-115">add</span><span class="sxs-lookup"><span data-stu-id="856a7-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="856a7-116">Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="856a7-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="856a7-117">clear</span><span class="sxs-lookup"><span data-stu-id="856a7-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="856a7-118">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="856a7-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="856a7-119">remove</span><span class="sxs-lookup"><span data-stu-id="856a7-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="856a7-120">Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="856a7-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="856a7-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="856a7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="856a7-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="856a7-122">**Element**</span></span>|<span data-ttu-id="856a7-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="856a7-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="856a7-124">system.net</span><span class="sxs-lookup"><span data-stu-id="856a7-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="856a7-125">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="856a7-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="856a7-126">Notes</span><span class="sxs-lookup"><span data-stu-id="856a7-126">Remarks</span></span>  
 <span data-ttu-id="856a7-127">L’élément `connectionManagement` définit le nombre maximal de connexions à un serveur ou à un groupe de serveurs.</span><span class="sxs-lookup"><span data-stu-id="856a7-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="856a7-128">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="856a7-128">Configuration Files</span></span>  
 <span data-ttu-id="856a7-129">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="856a7-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="856a7-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="856a7-130">Example</span></span>  
 <span data-ttu-id="856a7-131">L’exemple suivant configure une application pour qu’elle utilise quatre connexions au serveur `www.contoso.com` et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="856a7-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="856a7-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="856a7-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="856a7-133">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="856a7-133">Network Settings Schema</span></span>](index.md)
