---
title: <add> de <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398376"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="14b68-102">\<add> de \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="14b68-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="14b68-103">Spécifie un compte d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="14b68-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="14b68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14b68-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14b68-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="14b68-105">Attributes and Elements</span></span>  
 <span data-ttu-id="14b68-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="14b68-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14b68-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="14b68-107">Attributes</span></span>  
  
|<span data-ttu-id="14b68-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="14b68-108">Attribute</span></span>|<span data-ttu-id="14b68-109">Description</span><span class="sxs-lookup"><span data-stu-id="14b68-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14b68-110">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="14b68-110">securityIdentifier</span></span>|<span data-ttu-id="14b68-111">Chaîne indiquant un identificateur unique utilisée pour identifier un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="14b68-111">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="14b68-112">Les valeurs par défaut sont LocalSystem, Administrateurs, NS, LS et IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="14b68-112">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14b68-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="14b68-113">Child Elements</span></span>  
 <span data-ttu-id="14b68-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="14b68-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14b68-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="14b68-115">Parent Elements</span></span>  
  
|<span data-ttu-id="14b68-116">Élément</span><span class="sxs-lookup"><span data-stu-id="14b68-116">Element</span></span>|<span data-ttu-id="14b68-117">Description</span><span class="sxs-lookup"><span data-stu-id="14b68-117">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="14b68-118">Collection d’éléments de configuration qui contiennent un `securityIdentifier` attribut permettant de spécifier des comptes d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="14b68-118">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="14b68-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="14b68-119">Example</span></span>  
 <span data-ttu-id="14b68-120">L’exemple de configuration suivant ajoute à cette collection les cinq identificateurs par défaut correspondant aux comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="14b68-120">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="14b68-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14b68-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
