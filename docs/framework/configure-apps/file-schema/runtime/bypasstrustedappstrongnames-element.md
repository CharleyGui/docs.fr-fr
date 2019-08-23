---
title: Élément <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92873277b4b25e4c1c5981628187078ac7cb5704
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920888"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="95e97-102">\<bypassTrustedAppStrongNames>, élément</span><span class="sxs-lookup"><span data-stu-id="95e97-102">\<bypassTrustedAppStrongNames> Element</span></span>
<span data-ttu-id="95e97-103">Spécifie s’il faut ignorer la validation des noms forts sur les assemblys de confiance totale qui sont chargés dans un <xref:System.AppDomain>niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="95e97-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="95e97-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="95e97-104">\<configuration></span></span>  
<span data-ttu-id="95e97-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="95e97-105">\<runtime></span></span>  
<span data-ttu-id="95e97-106">\<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="95e97-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e97-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95e97-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95e97-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="95e97-108">Attributes and Elements</span></span>  
 <span data-ttu-id="95e97-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="95e97-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95e97-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="95e97-110">Attributes</span></span>  
  
|<span data-ttu-id="95e97-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="95e97-111">Attribute</span></span>|<span data-ttu-id="95e97-112">Description</span><span class="sxs-lookup"><span data-stu-id="95e97-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="95e97-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="95e97-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="95e97-114">Spécifie si la fonctionnalité de contournement qui évite de valider des noms forts pour les assemblys de confiance totale est activée.</span><span class="sxs-lookup"><span data-stu-id="95e97-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="95e97-115">Lorsque cette fonctionnalité est activée, les noms forts ne sont pas validés pour être corrects lorsque l’assembly est chargé.</span><span class="sxs-lookup"><span data-stu-id="95e97-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="95e97-116">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="95e97-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="95e97-117">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="95e97-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="95e97-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="95e97-118">Value</span></span>|<span data-ttu-id="95e97-119">Description</span><span class="sxs-lookup"><span data-stu-id="95e97-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="95e97-120">Les signatures avec nom fort sur les assemblys de confiance totale ne sont pas validées lorsque les assemblys sont chargés dans <xref:System.AppDomain>un niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="95e97-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="95e97-121">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="95e97-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="95e97-122">Les signatures avec nom fort sur les assemblys de confiance totale sont validées lorsque les assemblys sont chargés dans un <xref:System.AppDomain>niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="95e97-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="95e97-123">La signature de nom fort est vérifiée uniquement pour l’exactitude de la signature; elle n’est pas comparée à un autre nom fort pour une correspondance.</span><span class="sxs-lookup"><span data-stu-id="95e97-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95e97-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="95e97-124">Child Elements</span></span>  
 <span data-ttu-id="95e97-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="95e97-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95e97-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="95e97-126">Parent Elements</span></span>  
  
|<span data-ttu-id="95e97-127">Élément</span><span class="sxs-lookup"><span data-stu-id="95e97-127">Element</span></span>|<span data-ttu-id="95e97-128">Description</span><span class="sxs-lookup"><span data-stu-id="95e97-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="95e97-129">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95e97-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="95e97-130">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="95e97-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95e97-131">Notes</span><span class="sxs-lookup"><span data-stu-id="95e97-131">Remarks</span></span>  
 <span data-ttu-id="95e97-132">La fonctionnalité de contournement de nom fort évite la surcharge liée à la vérification de signature de nom fort des assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="95e97-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="95e97-133">Cette fonctionnalité s'applique à tout assembly signé avec un nom fort qui présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="95e97-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
- <span data-ttu-id="95e97-134">Confiance totale sans <xref:System.Security.Policy.StrongName> preuve (par exemple, a `MyComputer` une preuve de zone).</span><span class="sxs-lookup"><span data-stu-id="95e97-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
- <span data-ttu-id="95e97-135">Chargé dans un <xref:System.AppDomain> de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="95e97-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="95e97-136">Chargé à partir d'un emplacement sous la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> de cet <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="95e97-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="95e97-137">Sans signature différée.</span><span class="sxs-lookup"><span data-stu-id="95e97-137">Not delay-signed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95e97-138">Si la fonctionnalité de contournement a été désactivée pour toutes les applications sur l’ordinateur à l’aide d’une clé de Registre, ce paramètre de fichier de configuration n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="95e97-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="95e97-139">Pour plus d’informations, consultez [Guide pratique pour Désactiver la fonctionnalité consistant à ignorer les noms forts](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="95e97-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95e97-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="95e97-140">Example</span></span>  
 <span data-ttu-id="95e97-141">L’exemple suivant montre comment spécifier le comportement qui valide la signature de nom fort sur les assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="95e97-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95e97-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95e97-142">See also</span></span>

- [<span data-ttu-id="95e97-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="95e97-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="95e97-144">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="95e97-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="95e97-145">Guide pratique : désactiver la fonctionnalité consistant à ignorer les noms forts</span><span class="sxs-lookup"><span data-stu-id="95e97-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)
