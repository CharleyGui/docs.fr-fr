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
ms.openlocfilehash: 446bec116118ee8b604ef3664a6eb0452e6d5a38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184103"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="6f8b7-102">\<clear>, élément de connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6f8b7-102">\<clear> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="6f8b7-103">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="6f8b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f8b7-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f8b7-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6f8b7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6f8b7-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f8b7-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6f8b7-107">Attributes</span></span>  

 <span data-ttu-id="6f8b7-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f8b7-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6f8b7-109">Child Elements</span></span>  

 <span data-ttu-id="6f8b7-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f8b7-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6f8b7-111">Parent Elements</span></span>  
  
|<span data-ttu-id="6f8b7-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="6f8b7-112">**Element**</span></span>|<span data-ttu-id="6f8b7-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="6f8b7-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6f8b7-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="6f8b7-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="6f8b7-115">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f8b7-116">Notes</span><span class="sxs-lookup"><span data-stu-id="6f8b7-116">Remarks</span></span>  

 <span data-ttu-id="6f8b7-117">L' `clear` élément efface toutes les entrées de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6f8b7-118">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6f8b7-118">Configuration Files</span></span>  

 <span data-ttu-id="6f8b7-119">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6f8b7-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f8b7-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f8b7-120">Example</span></span>  

 <span data-ttu-id="6f8b7-121">L’exemple suivant efface la liste de gestion des connexions, puis ajoute de nouvelles entrées de gestion des connexions pour le serveur `www.contoso.com` et tous les autres hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f8b7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f8b7-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="6f8b7-123">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="6f8b7-123">Network Settings Schema</span></span>](index.md)
