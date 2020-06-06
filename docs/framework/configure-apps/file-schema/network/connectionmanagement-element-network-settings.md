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
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154892"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="6bb22-102">\<connectionManagement>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6bb22-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="6bb22-103">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="6bb22-103">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="6bb22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bb22-104">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bb22-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6bb22-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6bb22-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6bb22-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bb22-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6bb22-107">Attributes</span></span>  
 <span data-ttu-id="6bb22-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6bb22-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6bb22-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6bb22-109">Child Elements</span></span>  
  
|<span data-ttu-id="6bb22-110">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="6bb22-110">**Element**</span></span>|<span data-ttu-id="6bb22-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="6bb22-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6bb22-112">add</span><span class="sxs-lookup"><span data-stu-id="6bb22-112">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="6bb22-113">Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="6bb22-113">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="6bb22-114">clear</span><span class="sxs-lookup"><span data-stu-id="6bb22-114">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="6bb22-115">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="6bb22-115">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="6bb22-116">remove</span><span class="sxs-lookup"><span data-stu-id="6bb22-116">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="6bb22-117">Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="6bb22-117">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6bb22-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6bb22-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6bb22-119">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="6bb22-119">**Element**</span></span>|<span data-ttu-id="6bb22-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="6bb22-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6bb22-121">system.net</span><span class="sxs-lookup"><span data-stu-id="6bb22-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="6bb22-122">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="6bb22-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bb22-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="6bb22-123">Remarks</span></span>  
 <span data-ttu-id="6bb22-124">L' `connectionManagement` élément définit le nombre maximal de connexions à un serveur ou à un groupe de serveurs.</span><span class="sxs-lookup"><span data-stu-id="6bb22-124">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6bb22-125">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6bb22-125">Configuration Files</span></span>  
 <span data-ttu-id="6bb22-126">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6bb22-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bb22-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="6bb22-127">Example</span></span>  
 <span data-ttu-id="6bb22-128">L’exemple suivant configure une application pour qu’elle utilise quatre connexions au serveur `www.contoso.com` et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="6bb22-128">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6bb22-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bb22-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="6bb22-130">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="6bb22-130">Network Settings Schema</span></span>](index.md)
