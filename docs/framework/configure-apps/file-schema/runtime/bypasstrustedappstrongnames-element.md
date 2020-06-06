---
title: Élément <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739084"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="6a8f8-102">Élément \<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="6a8f8-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="6a8f8-103">Spécifie s’il faut ignorer la validation des noms forts sur les assemblys de confiance totale qui sont chargés dans un niveau de confiance totale <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="6a8f8-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="6a8f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a8f8-104">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a8f8-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6a8f8-105">Attributes and Elements</span></span>

<span data-ttu-id="6a8f8-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a8f8-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6a8f8-107">Attributes</span></span>

|<span data-ttu-id="6a8f8-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6a8f8-108">Attribute</span></span>|<span data-ttu-id="6a8f8-109">Description</span><span class="sxs-lookup"><span data-stu-id="6a8f8-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="6a8f8-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="6a8f8-111">Spécifie si la fonctionnalité de contournement qui évite de valider des noms forts pour les assemblys de confiance totale est activée.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-111">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="6a8f8-112">Lorsque cette fonctionnalité est activée, les noms forts ne sont pas validés pour être corrects lorsque l’assembly est chargé.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-112">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="6a8f8-113">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-113">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="6a8f8-114">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="6a8f8-114">enabled Attribute</span></span>

|<span data-ttu-id="6a8f8-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="6a8f8-115">Value</span></span>|<span data-ttu-id="6a8f8-116">Description</span><span class="sxs-lookup"><span data-stu-id="6a8f8-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="6a8f8-117">Les signatures avec nom fort sur les assemblys de confiance totale ne sont pas validées lorsque les assemblys sont chargés dans un niveau de confiance totale <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="6a8f8-117">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="6a8f8-118">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-118">This is the default.</span></span>|
|`false`|<span data-ttu-id="6a8f8-119">Les signatures avec nom fort sur les assemblys de confiance totale sont validées lorsque les assemblys sont chargés dans un niveau de confiance totale <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="6a8f8-119">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="6a8f8-120">La signature de nom fort est vérifiée uniquement pour l’exactitude de la signature ; elle n’est pas comparée à un autre nom fort pour une correspondance.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-120">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6a8f8-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6a8f8-121">Child Elements</span></span>

<span data-ttu-id="6a8f8-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a8f8-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6a8f8-123">Parent Elements</span></span>

|<span data-ttu-id="6a8f8-124">Élément</span><span class="sxs-lookup"><span data-stu-id="6a8f8-124">Element</span></span>|<span data-ttu-id="6a8f8-125">Description</span><span class="sxs-lookup"><span data-stu-id="6a8f8-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="6a8f8-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="6a8f8-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a8f8-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="6a8f8-128">Remarks</span></span>

<span data-ttu-id="6a8f8-129">La fonctionnalité de contournement de nom fort évite la surcharge liée à la vérification de signature de nom fort des assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-129">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="6a8f8-130">Cette fonctionnalité s’applique à tout assembly signé avec un nom fort qui présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a8f8-130">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="6a8f8-131">Confiance totale sans <xref:System.Security.Policy.StrongName> preuve (par exemple, a une `MyComputer` preuve de zone).</span><span class="sxs-lookup"><span data-stu-id="6a8f8-131">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="6a8f8-132">Chargé dans un <xref:System.AppDomain> de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-132">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="6a8f8-133">Chargé à partir d'un emplacement sous la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> de cet <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-133">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="6a8f8-134">Sans signature différée.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-134">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="6a8f8-135">Si la fonctionnalité de contournement a été désactivée pour toutes les applications sur l’ordinateur à l’aide d’une clé de Registre, ce paramètre de fichier de configuration n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-135">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="6a8f8-136">Pour plus d’informations, consultez [Comment : désactiver la fonctionnalité de contournement de nom fort](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="6a8f8-136">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a8f8-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a8f8-137">Example</span></span>

<span data-ttu-id="6a8f8-138">L’exemple suivant montre comment spécifier le comportement qui valide la signature de nom fort sur les assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="6a8f8-138">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6a8f8-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a8f8-139">See also</span></span>

- [<span data-ttu-id="6a8f8-140">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="6a8f8-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6a8f8-141">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6a8f8-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6a8f8-142">Comment : désactiver la fonctionnalité de contournement de nom fort</span><span class="sxs-lookup"><span data-stu-id="6a8f8-142">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
