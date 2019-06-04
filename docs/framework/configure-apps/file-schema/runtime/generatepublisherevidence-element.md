---
title: Élément <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0861436ca727d63cdae58e3222826bf6414610
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489440"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="4e422-102">\<generatePublisherEvidence > élément</span><span class="sxs-lookup"><span data-stu-id="4e422-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="4e422-103">Spécifie si le runtime crée <xref:System.Security.Policy.Publisher> preuve pour la sécurité d’accès de code (CAS).</span><span class="sxs-lookup"><span data-stu-id="4e422-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="4e422-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4e422-104">\<configuration></span></span>  
<span data-ttu-id="4e422-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="4e422-105">\<runtime></span></span>  
<span data-ttu-id="4e422-106">\<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="4e422-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e422-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e422-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e422-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e422-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4e422-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4e422-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e422-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e422-110">Attributes</span></span>  
  
|<span data-ttu-id="4e422-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e422-111">Attribute</span></span>|<span data-ttu-id="4e422-112">Description</span><span class="sxs-lookup"><span data-stu-id="4e422-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4e422-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4e422-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4e422-114">Spécifie si le runtime crée <xref:System.Security.Policy.Publisher> preuve.</span><span class="sxs-lookup"><span data-stu-id="4e422-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4e422-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="4e422-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4e422-116">Value</span><span class="sxs-lookup"><span data-stu-id="4e422-116">Value</span></span>|<span data-ttu-id="4e422-117">Description</span><span class="sxs-lookup"><span data-stu-id="4e422-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4e422-118">Ne crée pas <xref:System.Security.Policy.Publisher> preuve.</span><span class="sxs-lookup"><span data-stu-id="4e422-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="4e422-119">Crée <xref:System.Security.Policy.Publisher> preuve.</span><span class="sxs-lookup"><span data-stu-id="4e422-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="4e422-120">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4e422-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e422-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e422-121">Child Elements</span></span>  
 <span data-ttu-id="4e422-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4e422-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e422-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e422-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4e422-124">Élément</span><span class="sxs-lookup"><span data-stu-id="4e422-124">Element</span></span>|<span data-ttu-id="4e422-125">Description</span><span class="sxs-lookup"><span data-stu-id="4e422-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4e422-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e422-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4e422-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="4e422-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e422-128">Notes</span><span class="sxs-lookup"><span data-stu-id="4e422-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e422-129">Dans le .NET Framework 4 et versions ultérieures, cet élément n’a aucun effet sur les temps de chargement d’assembly.</span><span class="sxs-lookup"><span data-stu-id="4e422-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="4e422-130">Pour plus d’informations, consultez la section « Simplification de la stratégie sécurité » dans [modifications de sécurité](../../../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="4e422-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="4e422-131">Le common language runtime (CLR) essaie de vérifier la signature Authenticode au moment du chargement pour créer <xref:System.Security.Policy.Publisher> preuve pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4e422-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="4e422-132">Toutefois, par défaut, la plupart des applications ne doivent pas <xref:System.Security.Policy.Publisher> preuve.</span><span class="sxs-lookup"><span data-stu-id="4e422-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="4e422-133">La stratégie CAS standard ne repose pas sur le <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="4e422-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="4e422-134">Vous devez éviter le coût de démarrage inutile associé à la vérification de la signature de serveur de publication, sauf si votre application s’exécute sur un ordinateur avec la stratégie CAS personnalisée ou projette de répondre aux exigences pour <xref:System.Security.Permissions.PublisherIdentityPermission> dans un environnement de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="4e422-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="4e422-135">(Demandes d’autorisations d’identité aboutissent toujours dans un environnement de confiance totale.)</span><span class="sxs-lookup"><span data-stu-id="4e422-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e422-136">Nous recommandons que les services utilisent le `<generatePublisherEvidence>` élément pour améliorer les performances de démarrage.</span><span class="sxs-lookup"><span data-stu-id="4e422-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="4e422-137">À l’aide de cet élément peut également aider à éviter les retards qui peuvent entraîner un délai d’attente et l’annulation du démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="4e422-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="4e422-138">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="4e422-138">Configuration File</span></span>  
 <span data-ttu-id="4e422-139">Cet élément peut être utilisé uniquement dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="4e422-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e422-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e422-140">Example</span></span>  
 <span data-ttu-id="4e422-141">L’exemple suivant montre comment utiliser le `<generatePublisherEvidence>` élément pour désactiver la vérification de la stratégie de serveur de publication d’autorités de certification pour une application.</span><span class="sxs-lookup"><span data-stu-id="4e422-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e422-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e422-142">See also</span></span>

- [<span data-ttu-id="4e422-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="4e422-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="4e422-144">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="4e422-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
