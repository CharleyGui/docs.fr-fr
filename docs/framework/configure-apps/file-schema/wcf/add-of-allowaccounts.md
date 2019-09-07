---
title: <add> de <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398376"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="dcfeb-102">\<Ajouter > de \<la > allowAccounts</span><span class="sxs-lookup"><span data-stu-id="dcfeb-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="dcfeb-103">Spécifie un compte d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="dcfeb-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="dcfeb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dcfeb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dcfeb-105">&nbsp;&nbsp;[ **\<System. serviceModel. activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="dcfeb-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="dcfeb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> net. pipe**](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="dcfeb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="dcfeb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<allowAccounts >** ](allowaccounts.md)</span><span class="sxs-lookup"><span data-stu-id="dcfeb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)</span></span>\
<span data-ttu-id="dcfeb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="dcfeb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcfeb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcfeb-109">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcfeb-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dcfeb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dcfeb-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dcfeb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcfeb-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="dcfeb-112">Attributes</span></span>  
  
|<span data-ttu-id="dcfeb-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="dcfeb-113">Attribute</span></span>|<span data-ttu-id="dcfeb-114">Description</span><span class="sxs-lookup"><span data-stu-id="dcfeb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcfeb-115">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="dcfeb-115">securityIdentifier</span></span>|<span data-ttu-id="dcfeb-116">Chaîne indiquant un identificateur unique utilisée pour identifier un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dcfeb-116">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="dcfeb-117">Les valeurs par défaut sont LocalSystem, Administrateurs, NS, LS et IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="dcfeb-117">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcfeb-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dcfeb-118">Child Elements</span></span>  
 <span data-ttu-id="dcfeb-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dcfeb-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcfeb-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dcfeb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="dcfeb-121">Élément</span><span class="sxs-lookup"><span data-stu-id="dcfeb-121">Element</span></span>|<span data-ttu-id="dcfeb-122">Description</span><span class="sxs-lookup"><span data-stu-id="dcfeb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcfeb-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="dcfeb-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="dcfeb-124">Collection d’éléments de configuration qui contiennent un `securityIdentifier` attribut permettant de spécifier des comptes d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="dcfeb-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dcfeb-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="dcfeb-125">Example</span></span>  
 <span data-ttu-id="dcfeb-126">L’exemple de configuration suivant ajoute à cette collection les cinq identificateurs par défaut correspondant aux comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="dcfeb-126">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a><span data-ttu-id="dcfeb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcfeb-127">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
