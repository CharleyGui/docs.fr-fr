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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088484"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="44672-102">\<clear>, élément de connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="44672-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="44672-103">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="44672-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="44672-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44672-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44672-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="44672-105">Attributes and Elements</span></span>  
 <span data-ttu-id="44672-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="44672-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44672-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="44672-107">Attributes</span></span>  
 <span data-ttu-id="44672-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="44672-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44672-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="44672-109">Child Elements</span></span>  
 <span data-ttu-id="44672-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="44672-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44672-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="44672-111">Parent Elements</span></span>  
  
|<span data-ttu-id="44672-112">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="44672-112">**Element**</span></span>|<span data-ttu-id="44672-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="44672-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="44672-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="44672-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="44672-115">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="44672-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44672-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="44672-116">Remarks</span></span>  
 <span data-ttu-id="44672-117">L' `clear` élément efface toutes les entrées de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="44672-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="44672-118">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="44672-118">Configuration Files</span></span>  
 <span data-ttu-id="44672-119">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="44672-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44672-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="44672-120">Example</span></span>  
 <span data-ttu-id="44672-121">L’exemple suivant efface la liste de gestion des connexions, puis ajoute de nouvelles entrées de gestion des connexions pour le serveur `www.contoso.com` et tous les autres hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="44672-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44672-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44672-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="44672-123">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="44672-123">Network Settings Schema</span></span>](index.md)
