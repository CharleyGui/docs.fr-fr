---
title: <clear>, élément de connectionManagement (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: 17b380b12977423669fd413132d69a3082daca41
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698356"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="0c9e9-102">\<clear > élément pour connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="0c9e9-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="0c9e9-103">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="0c9e9-103">Clears the connection management list.</span></span>  
  
[<span data-ttu-id="0c9e9-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="0c9e9-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0c9e9-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0c9e9-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="0c9e9-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0c9e9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="0c9e9-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="0c9e9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c9e9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c9e9-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c9e9-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c9e9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0c9e9-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c9e9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c9e9-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c9e9-111">Attributes</span></span>  
 <span data-ttu-id="0c9e9-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0c9e9-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c9e9-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c9e9-113">Child Elements</span></span>  
 <span data-ttu-id="0c9e9-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0c9e9-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c9e9-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c9e9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0c9e9-116">**Élément**</span><span class="sxs-lookup"><span data-stu-id="0c9e9-116">**Element**</span></span>|<span data-ttu-id="0c9e9-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="0c9e9-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0c9e9-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="0c9e9-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="0c9e9-119">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="0c9e9-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c9e9-120">Notes</span><span class="sxs-lookup"><span data-stu-id="0c9e9-120">Remarks</span></span>  
 <span data-ttu-id="0c9e9-121">L’élément `clear` efface toutes les entrées de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="0c9e9-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0c9e9-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0c9e9-122">Configuration Files</span></span>  
 <span data-ttu-id="0c9e9-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0c9e9-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c9e9-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c9e9-124">Example</span></span>  
 <span data-ttu-id="0c9e9-125">L’exemple suivant efface la liste de gestion des connexions, puis ajoute de nouvelles entrées de gestion des connexions pour le serveur `www.contoso.com` et tous les autres hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="0c9e9-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c9e9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c9e9-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="0c9e9-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="0c9e9-127">Network Settings Schema</span></span>](index.md)
