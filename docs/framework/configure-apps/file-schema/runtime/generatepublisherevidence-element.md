---
title: Élément <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 24a5ea02992a5bce681b5bab4fb7f75505bd225d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154112"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="5a4fe-102">\<generatePublisherEvidence> Element</span><span class="sxs-lookup"><span data-stu-id="5a4fe-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="5a4fe-103">Précise si le temps <xref:System.Security.Policy.Publisher> d’exécution crée des preuves pour la sécurité d’accès au code (CAS).</span><span class="sxs-lookup"><span data-stu-id="5a4fe-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="5a4fe-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a4fe-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a4fe-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a4fe-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5a4fe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<générerPublisherEvidence>**</span><span class="sxs-lookup"><span data-stu-id="5a4fe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4fe-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a4fe-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a4fe-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5a4fe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a4fe-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a4fe-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5a4fe-110">Attributes</span></span>  
  
|<span data-ttu-id="5a4fe-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a4fe-111">Attribute</span></span>|<span data-ttu-id="5a4fe-112">Description</span><span class="sxs-lookup"><span data-stu-id="5a4fe-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5a4fe-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a4fe-114">Précise si le temps <xref:System.Security.Policy.Publisher> d’exécution crée des preuves.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5a4fe-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="5a4fe-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5a4fe-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="5a4fe-116">Value</span></span>|<span data-ttu-id="5a4fe-117">Description</span><span class="sxs-lookup"><span data-stu-id="5a4fe-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5a4fe-118">Ne crée <xref:System.Security.Policy.Publisher> pas de preuves.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="5a4fe-119">Crée <xref:System.Security.Policy.Publisher> des preuves.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="5a4fe-120">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a4fe-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a4fe-121">Child Elements</span></span>  
 <span data-ttu-id="5a4fe-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a4fe-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a4fe-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5a4fe-124">Élément</span><span class="sxs-lookup"><span data-stu-id="5a4fe-124">Element</span></span>|<span data-ttu-id="5a4fe-125">Description</span><span class="sxs-lookup"><span data-stu-id="5a4fe-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a4fe-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5a4fe-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a4fe-128">Notes </span><span class="sxs-lookup"><span data-stu-id="5a4fe-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a4fe-129">Dans le cadre .NET 4 et plus tard, cet élément n’a aucun effet sur les temps de chargement d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="5a4fe-130">Pour plus d’informations, consultez la section « Simplification de la politique de sécurité » dans [les changements de sécurité](../../../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="5a4fe-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="5a4fe-131">Le temps courant de course de langue (CLR) essaye <xref:System.Security.Policy.Publisher> de vérifier la signature Authenticode au moment de la charge pour créer des preuves pour l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="5a4fe-132">Toutefois, par défaut, la <xref:System.Security.Policy.Publisher> plupart des applications n’ont pas besoin de preuves.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="5a4fe-133">La politique standard de <xref:System.Security.Policy.PublisherMembershipCondition>la SAE ne repose pas sur le .</span><span class="sxs-lookup"><span data-stu-id="5a4fe-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="5a4fe-134">Vous devez éviter les coûts inutiles de démarrage associés à la vérification de la signature de l’éditeur <xref:System.Security.Permissions.PublisherIdentityPermission> à moins que votre application ne s’exécute sur un ordinateur avec la politique de CAS personnalisée, ou a l’intention de satisfaire les demandes dans un environnement de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="5a4fe-135">(Les demandes d’autorisations d’identité réussissent toujours dans un environnement de confiance.)</span><span class="sxs-lookup"><span data-stu-id="5a4fe-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a4fe-136">Nous recommandons que `<generatePublisherEvidence>` les services utilisent cet élément pour améliorer les performances des startups.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="5a4fe-137">L’utilisation de cet élément peut également aider à éviter les retards qui peuvent entraîner un délai d’utilisation et l’annulation de la start-up de service.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5a4fe-138">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="5a4fe-138">Configuration File</span></span>  
 <span data-ttu-id="5a4fe-139">Cet élément ne peut être utilisé que dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a4fe-140"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5a4fe-140">Example</span></span>  
 <span data-ttu-id="5a4fe-141">L’exemple suivant montre `<generatePublisherEvidence>` comment utiliser l’élément pour désactiver la vérification de la politique d’éditeur de la SAE pour une demande.</span><span class="sxs-lookup"><span data-stu-id="5a4fe-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a4fe-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a4fe-142">See also</span></span>

- [<span data-ttu-id="5a4fe-143">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="5a4fe-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5a4fe-144">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="5a4fe-144">Configuration File Schema</span></span>](../index.md)
