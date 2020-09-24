---
title: <add>, élément de connectionManagement (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 05e4a1bc42dc39c7d2b56e30c98bdeefd31e4416
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149476"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="d49c4-102">\<add>, élément de connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="d49c4-102">\<add> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="d49c4-103">Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="d49c4-103">Adds an IP address or DNS name to the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="d49c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d49c4-104">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d49c4-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d49c4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d49c4-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d49c4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d49c4-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="d49c4-107">Attributes</span></span>  
  
|<span data-ttu-id="d49c4-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="d49c4-108">**Attribute**</span></span>|<span data-ttu-id="d49c4-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="d49c4-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="d49c4-110">Chaîne décrivant une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="d49c4-110">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="d49c4-111">Nombre maximal de connexions à un serveur.</span><span class="sxs-lookup"><span data-stu-id="d49c4-111">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="d49c4-112">Si aucune valeur n'est indiquée, la valeur par défaut 2 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d49c4-112">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d49c4-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d49c4-113">Child Elements</span></span>  

 <span data-ttu-id="d49c4-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d49c4-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d49c4-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d49c4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d49c4-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="d49c4-116">**Element**</span></span>|<span data-ttu-id="d49c4-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="d49c4-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d49c4-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="d49c4-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="d49c4-119">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="d49c4-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d49c4-120">Notes</span><span class="sxs-lookup"><span data-stu-id="d49c4-120">Remarks</span></span>  

 <span data-ttu-id="d49c4-121">La valeur de l'attribut `address` doit être un astérisque pour spécifier toutes les connexions, ou une chaîne au format `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="d49c4-121">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="d49c4-122">Si l'URI passé à une API HTTP contient des caractères Unicode, le nom est converti en interne à l'aide de <xref:System.Uri.DnsSafeHost%2A> qui peut éventuellement retourner une chaîne Punycode (le comportement dépend de la configuration IDN actuelle).</span><span class="sxs-lookup"><span data-stu-id="d49c4-122">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d49c4-123">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d49c4-123">Configuration Files</span></span>  

 <span data-ttu-id="d49c4-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d49c4-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d49c4-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="d49c4-125">Example</span></span>  

 <span data-ttu-id="d49c4-126">L’exemple suivant configure une application pour qu’elle utilise quatre connexions au serveur `www.contoso.com` et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="d49c4-126">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d49c4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d49c4-127">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="d49c4-128">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="d49c4-128">Network Settings Schema</span></span>](index.md)
