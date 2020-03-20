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
ms.openlocfilehash: 093b68d31e03094bedefa96a2f2d53eb3d84edf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155009"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="b18da-102">\<ajouter> Element pour la connexionManagement (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b18da-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="b18da-103">Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="b18da-103">Adds an IP address or DNS name to the connection management list.</span></span>  

<span data-ttu-id="b18da-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b18da-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b18da-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b18da-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="b18da-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connexionManagement>**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b18da-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="b18da-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="b18da-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b18da-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b18da-108">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b18da-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b18da-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b18da-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b18da-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b18da-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="b18da-111">Attributes</span></span>  
  
|<span data-ttu-id="b18da-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="b18da-112">**Attribute**</span></span>|<span data-ttu-id="b18da-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="b18da-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="b18da-114">Chaîne décrivant une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="b18da-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="b18da-115">Nombre maximal de connexions à un serveur.</span><span class="sxs-lookup"><span data-stu-id="b18da-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="b18da-116">Si aucune valeur n'est indiquée, la valeur par défaut 2 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b18da-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b18da-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b18da-117">Child Elements</span></span>  
 <span data-ttu-id="b18da-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b18da-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b18da-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b18da-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b18da-120">**Élément**</span><span class="sxs-lookup"><span data-stu-id="b18da-120">**Element**</span></span>|<span data-ttu-id="b18da-121">**Description**</span><span class="sxs-lookup"><span data-stu-id="b18da-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b18da-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="b18da-122">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="b18da-123">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="b18da-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b18da-124">Notes </span><span class="sxs-lookup"><span data-stu-id="b18da-124">Remarks</span></span>  
 <span data-ttu-id="b18da-125">La valeur de l'attribut `address` doit être un astérisque pour spécifier toutes les connexions, ou une chaîne au format `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="b18da-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="b18da-126">Si l'URI passé à une API HTTP contient des caractères Unicode, le nom est converti en interne à l'aide de <xref:System.Uri.DnsSafeHost%2A> qui peut éventuellement retourner une chaîne Punycode (le comportement dépend de la configuration IDN actuelle).</span><span class="sxs-lookup"><span data-stu-id="b18da-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b18da-127">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b18da-127">Configuration Files</span></span>  
 <span data-ttu-id="b18da-128">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b18da-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b18da-129"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b18da-129">Example</span></span>  
 <span data-ttu-id="b18da-130">L’exemple suivant configure une application pour `www.contoso.com` utiliser quatre connexions au serveur et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="b18da-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b18da-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b18da-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="b18da-132">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="b18da-132">Network Settings Schema</span></span>](index.md)
