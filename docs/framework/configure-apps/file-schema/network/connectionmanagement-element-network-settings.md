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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154892"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="59ccd-102">\<connectionManagement>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="59ccd-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="59ccd-103">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="59ccd-103">Specifies the maximum number of connections to a network host.</span></span>  

<span data-ttu-id="59ccd-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="59ccd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="59ccd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="59ccd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="59ccd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connexionManagement>**</span><span class="sxs-lookup"><span data-stu-id="59ccd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**</span></span>

## <a name="syntax"></a><span data-ttu-id="59ccd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59ccd-107">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59ccd-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="59ccd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="59ccd-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="59ccd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59ccd-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="59ccd-110">Attributes</span></span>  
 <span data-ttu-id="59ccd-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="59ccd-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59ccd-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="59ccd-112">Child Elements</span></span>  
  
|<span data-ttu-id="59ccd-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="59ccd-113">**Element**</span></span>|<span data-ttu-id="59ccd-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="59ccd-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="59ccd-115">ajouter</span><span class="sxs-lookup"><span data-stu-id="59ccd-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="59ccd-116">Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="59ccd-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="59ccd-117">Clair</span><span class="sxs-lookup"><span data-stu-id="59ccd-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="59ccd-118">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="59ccd-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="59ccd-119">retirer</span><span class="sxs-lookup"><span data-stu-id="59ccd-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="59ccd-120">Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="59ccd-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59ccd-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="59ccd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="59ccd-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="59ccd-122">**Element**</span></span>|<span data-ttu-id="59ccd-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="59ccd-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="59ccd-124">system.net</span><span class="sxs-lookup"><span data-stu-id="59ccd-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="59ccd-125">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="59ccd-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ccd-126">Notes </span><span class="sxs-lookup"><span data-stu-id="59ccd-126">Remarks</span></span>  
 <span data-ttu-id="59ccd-127">L’élément `connectionManagement` définit le nombre maximum de connexions vers un serveur ou un groupe de serveurs.</span><span class="sxs-lookup"><span data-stu-id="59ccd-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="59ccd-128">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="59ccd-128">Configuration Files</span></span>  
 <span data-ttu-id="59ccd-129">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="59ccd-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59ccd-130"> Exemple</span><span class="sxs-lookup"><span data-stu-id="59ccd-130">Example</span></span>  
 <span data-ttu-id="59ccd-131">L’exemple suivant configure une application pour `www.contoso.com` utiliser quatre connexions au serveur et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="59ccd-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59ccd-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59ccd-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="59ccd-133">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="59ccd-133">Network Settings Schema</span></span>](index.md)
