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
ms.openlocfilehash: 46157482d7ceb42b352c68dc9b0eab4f7688bc5c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176173"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="b5220-102">\<remove>, élément de connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b5220-102">\<remove> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="b5220-103">Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="b5220-103">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="b5220-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5220-104">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5220-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b5220-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b5220-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b5220-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5220-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b5220-107">Attributes</span></span>  
  
|<span data-ttu-id="b5220-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="b5220-108">**Attribute**</span></span>|<span data-ttu-id="b5220-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="b5220-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="b5220-110">Une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="b5220-110">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5220-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b5220-111">Child Elements</span></span>  

 <span data-ttu-id="b5220-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b5220-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5220-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b5220-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b5220-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="b5220-114">**Element**</span></span>|<span data-ttu-id="b5220-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="b5220-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b5220-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="b5220-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="b5220-117">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="b5220-117">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5220-118">Notes</span><span class="sxs-lookup"><span data-stu-id="b5220-118">Remarks</span></span>  

 <span data-ttu-id="b5220-119">L' `remove` élément supprime l’entrée de la liste de gestion des connexions pour le serveur spécifié.</span><span class="sxs-lookup"><span data-stu-id="b5220-119">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="b5220-120">La valeur de l' `address` attribut doit être une adresse IP ou un nom d’hôte valide.</span><span class="sxs-lookup"><span data-stu-id="b5220-120">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b5220-121">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b5220-121">Configuration Files</span></span>  

 <span data-ttu-id="b5220-122">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b5220-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5220-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5220-123">Example</span></span>  

 <span data-ttu-id="b5220-124">L’exemple suivant supprime toutes les entrées de liste de gestion des connexions pour le serveur `www.adventure-works.com` , puis configure une application pour qu’elle utilise quatre connexions au serveur `www.contoso.com` et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="b5220-124">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5220-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5220-125">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="b5220-126">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="b5220-126">Network Settings Schema</span></span>](index.md)
