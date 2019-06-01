---
title: Élément <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8733e11aba30ebea30fc71a5350f76dfd041eb4
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456416"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="3fde2-102">\<legacyCorruptedStateExceptionsPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="3fde2-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="3fde2-103">Spécifie si le common language runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.</span><span class="sxs-lookup"><span data-stu-id="3fde2-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="3fde2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3fde2-104">\<configuration></span></span>  
<span data-ttu-id="3fde2-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="3fde2-105">\<runtime></span></span>  
<span data-ttu-id="3fde2-106">\<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="3fde2-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fde2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fde2-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fde2-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3fde2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3fde2-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3fde2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fde2-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3fde2-110">Attributes</span></span>  
  
|<span data-ttu-id="3fde2-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="3fde2-111">Attribute</span></span>|<span data-ttu-id="3fde2-112">Description</span><span class="sxs-lookup"><span data-stu-id="3fde2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3fde2-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="3fde2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3fde2-114">Spécifie que l’application interceptera endommager des échecs d’état d’exception telles que des violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="3fde2-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3fde2-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="3fde2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3fde2-116">Value</span><span class="sxs-lookup"><span data-stu-id="3fde2-116">Value</span></span>|<span data-ttu-id="3fde2-117">Description</span><span class="sxs-lookup"><span data-stu-id="3fde2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3fde2-118">L’application n’intercepte pas endommager les échecs d’état d’exception telles que des violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="3fde2-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="3fde2-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3fde2-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3fde2-120">L’application interceptera endommager des échecs d’état d’exception telles que des violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="3fde2-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3fde2-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3fde2-121">Child Elements</span></span>  
 <span data-ttu-id="3fde2-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3fde2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3fde2-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3fde2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3fde2-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3fde2-124">Element</span></span>|<span data-ttu-id="3fde2-125">Description</span><span class="sxs-lookup"><span data-stu-id="3fde2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3fde2-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3fde2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3fde2-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3fde2-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fde2-128">Notes</span><span class="sxs-lookup"><span data-stu-id="3fde2-128">Remarks</span></span>  
 <span data-ttu-id="3fde2-129">Dans le .NET Framework version 3.5 et versions antérieure, le common language runtime autorise le code managé intercepter les exceptions qui ont été générées par les États de processus endommagé.</span><span class="sxs-lookup"><span data-stu-id="3fde2-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="3fde2-130">Une violation d’accès est un exemple de ce type d’exception.</span><span class="sxs-lookup"><span data-stu-id="3fde2-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="3fde2-131">En commençant par le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]managé code n’intercepte plus ces types d’exceptions dans `catch` blocs.</span><span class="sxs-lookup"><span data-stu-id="3fde2-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="3fde2-132">Toutefois, vous pouvez remplacer cette modification et maintenir la gestion des exceptions d’état endommagé de deux manières :</span><span class="sxs-lookup"><span data-stu-id="3fde2-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="3fde2-133">Définir le `<legacyCorruptedStateExceptionsPolicy>` l’élément `enabled` attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="3fde2-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="3fde2-134">Ce paramètre de configuration est appliquée au niveau du processus et affecte toutes les méthodes.</span><span class="sxs-lookup"><span data-stu-id="3fde2-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="3fde2-135">ou</span><span class="sxs-lookup"><span data-stu-id="3fde2-135">-or-</span></span>  
  
- <span data-ttu-id="3fde2-136">Appliquer le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> d’attribut à la méthode qui contient les exceptions `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="3fde2-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="3fde2-137">Cet élément de configuration est disponible uniquement dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="3fde2-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fde2-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="3fde2-138">Example</span></span>  
 <span data-ttu-id="3fde2-139">L’exemple suivant montre comment spécifier que l’application doit rétablir le comportement avant le .NET Framework 4 et intercepter des échecs d’exception altérer tout état.</span><span class="sxs-lookup"><span data-stu-id="3fde2-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fde2-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fde2-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="3fde2-141">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="3fde2-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="3fde2-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3fde2-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
