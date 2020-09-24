---
title: Élément <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 506e7873fab8e41fce121587c22d85600a8b1760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158771"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="16bcb-102">Élément \<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="16bcb-102">\<generatePublisherEvidence> Element</span></span>

<span data-ttu-id="16bcb-103">Spécifie si le runtime crée une <xref:System.Security.Policy.Publisher> preuve pour la sécurité d’accès du code (cas).</span><span class="sxs-lookup"><span data-stu-id="16bcb-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="16bcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16bcb-104">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16bcb-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="16bcb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="16bcb-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="16bcb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16bcb-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="16bcb-107">Attributes</span></span>  
  
|<span data-ttu-id="16bcb-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="16bcb-108">Attribute</span></span>|<span data-ttu-id="16bcb-109">Description</span><span class="sxs-lookup"><span data-stu-id="16bcb-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="16bcb-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="16bcb-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="16bcb-111">Spécifie si le runtime crée une <xref:System.Security.Policy.Publisher> preuve.</span><span class="sxs-lookup"><span data-stu-id="16bcb-111">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="16bcb-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="16bcb-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="16bcb-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="16bcb-113">Value</span></span>|<span data-ttu-id="16bcb-114">Description</span><span class="sxs-lookup"><span data-stu-id="16bcb-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="16bcb-115">Ne crée pas de <xref:System.Security.Policy.Publisher> preuve.</span><span class="sxs-lookup"><span data-stu-id="16bcb-115">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="16bcb-116">Crée une <xref:System.Security.Policy.Publisher> preuve.</span><span class="sxs-lookup"><span data-stu-id="16bcb-116">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="16bcb-117">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="16bcb-117">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16bcb-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="16bcb-118">Child Elements</span></span>  

 <span data-ttu-id="16bcb-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="16bcb-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16bcb-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="16bcb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="16bcb-121">Élément</span><span class="sxs-lookup"><span data-stu-id="16bcb-121">Element</span></span>|<span data-ttu-id="16bcb-122">Description</span><span class="sxs-lookup"><span data-stu-id="16bcb-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16bcb-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16bcb-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16bcb-124">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="16bcb-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16bcb-125">Notes</span><span class="sxs-lookup"><span data-stu-id="16bcb-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16bcb-126">Dans le .NET Framework 4 et versions ultérieures, cet élément n’a aucun effet sur les temps de chargement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="16bcb-126">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="16bcb-127">Pour plus d’informations, consultez la section « simplification de la stratégie de sécurité » dans [modifications de sécurité](/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="16bcb-127">For more information, see the "Security Policy Simplification" section in [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="16bcb-128">Le common language runtime (CLR) tente de vérifier la signature Authenticode au moment du chargement pour créer <xref:System.Security.Policy.Publisher> la preuve de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="16bcb-128">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="16bcb-129">Toutefois, par défaut, la plupart des applications n’ont pas besoin de <xref:System.Security.Policy.Publisher> preuve.</span><span class="sxs-lookup"><span data-stu-id="16bcb-129">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="16bcb-130">La stratégie CAS standard ne repose pas sur <xref:System.Security.Policy.PublisherMembershipCondition> .</span><span class="sxs-lookup"><span data-stu-id="16bcb-130">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="16bcb-131">Vous devez éviter les coûts de démarrage inutiles associés à la vérification de la signature de l’éditeur, sauf si votre application s’exécute sur un ordinateur doté d’une stratégie CAS, ou s’il a l’intention de satisfaire les demandes de <xref:System.Security.Permissions.PublisherIdentityPermission> dans un environnement de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="16bcb-131">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="16bcb-132">(Les demandes d’autorisations d’identité fonctionnent toujours dans un environnement de confiance totale.)</span><span class="sxs-lookup"><span data-stu-id="16bcb-132">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16bcb-133">Nous recommandons que les services utilisent l' `<generatePublisherEvidence>` élément pour améliorer les performances de démarrage.</span><span class="sxs-lookup"><span data-stu-id="16bcb-133">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="16bcb-134">L’utilisation de cet élément peut également aider à éviter des retards qui peuvent entraîner un délai d’attente et l’annulation du démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="16bcb-134">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="16bcb-135">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="16bcb-135">Configuration File</span></span>  

 <span data-ttu-id="16bcb-136">Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="16bcb-136">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16bcb-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="16bcb-137">Example</span></span>  

 <span data-ttu-id="16bcb-138">L’exemple suivant montre comment utiliser l' `<generatePublisherEvidence>` élément pour désactiver la vérification de la stratégie d’éditeur cas pour une application.</span><span class="sxs-lookup"><span data-stu-id="16bcb-138">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16bcb-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16bcb-139">See also</span></span>

- [<span data-ttu-id="16bcb-140">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="16bcb-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16bcb-141">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="16bcb-141">Configuration File Schema</span></span>](../index.md)
