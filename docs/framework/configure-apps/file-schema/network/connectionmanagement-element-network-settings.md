---
title: <connectionManagement>, élément (paramètres réseau)
description: L' <connectionManagement> élément paramètres réseau spécifie le nombre maximal de connexions à un hôte réseau dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 52b780c739a00cb53694b547ee1a33c1b5d98c86
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167312"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="ea0d9-103">\<connectionManagement>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="ea0d9-103">\<connectionManagement> Element (Network Settings)</span></span>

<span data-ttu-id="ea0d9-104">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-104">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="ea0d9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea0d9-105">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea0d9-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ea0d9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ea0d9-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea0d9-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="ea0d9-108">Attributes</span></span>  

 <span data-ttu-id="ea0d9-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea0d9-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ea0d9-110">Child Elements</span></span>  
  
|<span data-ttu-id="ea0d9-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="ea0d9-111">**Element**</span></span>|<span data-ttu-id="ea0d9-112">**Description**</span><span class="sxs-lookup"><span data-stu-id="ea0d9-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ea0d9-113">add</span><span class="sxs-lookup"><span data-stu-id="ea0d9-113">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="ea0d9-114">Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-114">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="ea0d9-115">clear</span><span class="sxs-lookup"><span data-stu-id="ea0d9-115">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="ea0d9-116">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-116">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="ea0d9-117">remove</span><span class="sxs-lookup"><span data-stu-id="ea0d9-117">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="ea0d9-118">Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-118">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea0d9-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ea0d9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ea0d9-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="ea0d9-120">**Element**</span></span>|<span data-ttu-id="ea0d9-121">**Description**</span><span class="sxs-lookup"><span data-stu-id="ea0d9-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ea0d9-122">system.net</span><span class="sxs-lookup"><span data-stu-id="ea0d9-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="ea0d9-123">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea0d9-124">Notes</span><span class="sxs-lookup"><span data-stu-id="ea0d9-124">Remarks</span></span>  

 <span data-ttu-id="ea0d9-125">L' `connectionManagement` élément définit le nombre maximal de connexions à un serveur ou à un groupe de serveurs.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-125">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ea0d9-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ea0d9-126">Configuration Files</span></span>  

 <span data-ttu-id="ea0d9-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ea0d9-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea0d9-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea0d9-128">Example</span></span>  

 <span data-ttu-id="ea0d9-129">L’exemple suivant configure une application pour qu’elle utilise quatre connexions au serveur `www.contoso.com` et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="ea0d9-129">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea0d9-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea0d9-130">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="ea0d9-131">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="ea0d9-131">Network Settings Schema</span></span>](index.md)
