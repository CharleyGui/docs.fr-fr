---
title: Élément <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5314fe5927abf2d3855acb45c763507ab6cb3c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920746"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="53c3c-102">\<generatePublisherEvidence >, élément</span><span class="sxs-lookup"><span data-stu-id="53c3c-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="53c3c-103">Spécifie si le runtime <xref:System.Security.Policy.Publisher> crée une preuve pour la sécurité d’accès du code (cas).</span><span class="sxs-lookup"><span data-stu-id="53c3c-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="53c3c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="53c3c-104">\<configuration></span></span>  
<span data-ttu-id="53c3c-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="53c3c-105">\<runtime></span></span>  
<span data-ttu-id="53c3c-106">\<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="53c3c-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c3c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53c3c-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53c3c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="53c3c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="53c3c-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="53c3c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53c3c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="53c3c-110">Attributes</span></span>  
  
|<span data-ttu-id="53c3c-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="53c3c-111">Attribute</span></span>|<span data-ttu-id="53c3c-112">Description</span><span class="sxs-lookup"><span data-stu-id="53c3c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="53c3c-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="53c3c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="53c3c-114">Spécifie si le runtime <xref:System.Security.Policy.Publisher> crée une preuve.</span><span class="sxs-lookup"><span data-stu-id="53c3c-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="53c3c-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="53c3c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="53c3c-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="53c3c-116">Value</span></span>|<span data-ttu-id="53c3c-117">Description</span><span class="sxs-lookup"><span data-stu-id="53c3c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="53c3c-118">Ne crée <xref:System.Security.Policy.Publisher> pas de preuve.</span><span class="sxs-lookup"><span data-stu-id="53c3c-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="53c3c-119">Crée <xref:System.Security.Policy.Publisher> une preuve.</span><span class="sxs-lookup"><span data-stu-id="53c3c-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="53c3c-120">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="53c3c-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53c3c-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="53c3c-121">Child Elements</span></span>  
 <span data-ttu-id="53c3c-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="53c3c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53c3c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="53c3c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="53c3c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="53c3c-124">Element</span></span>|<span data-ttu-id="53c3c-125">Description</span><span class="sxs-lookup"><span data-stu-id="53c3c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="53c3c-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53c3c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="53c3c-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="53c3c-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53c3c-128">Notes</span><span class="sxs-lookup"><span data-stu-id="53c3c-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53c3c-129">Dans le .NET Framework 4 et versions ultérieures, cet élément n’a aucun effet sur les temps de chargement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="53c3c-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="53c3c-130">Pour plus d’informations, consultez la section «simplification de la stratégie de sécurité» dans [modifications de sécurité](../../../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="53c3c-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="53c3c-131">Le Common Language Runtime (CLR) tente de vérifier la signature Authenticode au moment du chargement pour <xref:System.Security.Policy.Publisher> créer la preuve de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="53c3c-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="53c3c-132">Toutefois, par défaut, la plupart des applications n' <xref:System.Security.Policy.Publisher> ont pas besoin de preuve.</span><span class="sxs-lookup"><span data-stu-id="53c3c-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="53c3c-133">La <xref:System.Security.Policy.PublisherMembershipCondition>stratégie cas standard ne repose pas sur.</span><span class="sxs-lookup"><span data-stu-id="53c3c-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="53c3c-134">Vous devez éviter les coûts de démarrage inutiles associés à la vérification de la signature de l’éditeur, sauf si votre application s’exécute sur un ordinateur doté d’une stratégie cas, ou s' <xref:System.Security.Permissions.PublisherIdentityPermission> il a l’intention de satisfaire les demandes de dans un environnement de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="53c3c-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="53c3c-135">(Les demandes d’autorisations d’identité fonctionnent toujours dans un environnement de confiance totale.)</span><span class="sxs-lookup"><span data-stu-id="53c3c-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53c3c-136">Nous recommandons que les services utilisent `<generatePublisherEvidence>` l’élément pour améliorer les performances de démarrage.</span><span class="sxs-lookup"><span data-stu-id="53c3c-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="53c3c-137">L’utilisation de cet élément peut également aider à éviter des retards qui peuvent entraîner un délai d’attente et l’annulation du démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="53c3c-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="53c3c-138">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="53c3c-138">Configuration File</span></span>  
 <span data-ttu-id="53c3c-139">Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="53c3c-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53c3c-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="53c3c-140">Example</span></span>  
 <span data-ttu-id="53c3c-141">L’exemple suivant montre comment utiliser l’élément `<generatePublisherEvidence>` pour désactiver la vérification de la stratégie d’éditeur cas pour une application.</span><span class="sxs-lookup"><span data-stu-id="53c3c-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53c3c-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53c3c-142">See also</span></span>

- [<span data-ttu-id="53c3c-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="53c3c-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="53c3c-144">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="53c3c-144">Configuration File Schema</span></span>](../index.md)
