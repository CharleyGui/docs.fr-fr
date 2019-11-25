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
ms.openlocfilehash: a76df48a9de084e1121a5e96b22edf7aa3acba23
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088484"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="3a11c-102">\<effacer l’élément > pour connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3a11c-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="3a11c-103">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="3a11c-103">Clears the connection management list.</span></span>  

<span data-ttu-id="3a11c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a11c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a11c-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3a11c-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="3a11c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement**](connectionmanagement-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="3a11c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="3a11c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Clear** ></span><span class="sxs-lookup"><span data-stu-id="3a11c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3a11c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a11c-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a11c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3a11c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3a11c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3a11c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a11c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3a11c-111">Attributes</span></span>  
 <span data-ttu-id="3a11c-112">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="3a11c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a11c-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3a11c-113">Child Elements</span></span>  
 <span data-ttu-id="3a11c-114">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="3a11c-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a11c-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3a11c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3a11c-116">**Élément**</span><span class="sxs-lookup"><span data-stu-id="3a11c-116">**Element**</span></span>|<span data-ttu-id="3a11c-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="3a11c-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3a11c-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="3a11c-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="3a11c-119">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="3a11c-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a11c-120">Notes</span><span class="sxs-lookup"><span data-stu-id="3a11c-120">Remarks</span></span>  
 <span data-ttu-id="3a11c-121">L’élément `clear` efface toutes les entrées de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="3a11c-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3a11c-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3a11c-122">Configuration Files</span></span>  
 <span data-ttu-id="3a11c-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="3a11c-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a11c-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a11c-124">Example</span></span>  
 <span data-ttu-id="3a11c-125">L’exemple suivant efface la liste de gestion des connexions, puis ajoute de nouvelles entrées de gestion des connexions pour le serveur `www.contoso.com` et tous les autres hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="3a11c-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a11c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a11c-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="3a11c-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3a11c-127">Network Settings Schema</span></span>](index.md)
