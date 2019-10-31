---
title: Élément <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116456"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="bba68-102">\<élément legacyCorruptedStateExceptionsPolicy ></span><span class="sxs-lookup"><span data-stu-id="bba68-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="bba68-103">Spécifie si le common language runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.</span><span class="sxs-lookup"><span data-stu-id="bba68-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
<span data-ttu-id="bba68-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bba68-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bba68-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="bba68-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="bba68-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyCorruptedStateExceptionsPolicy** ></span><span class="sxs-lookup"><span data-stu-id="bba68-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba68-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bba68-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bba68-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bba68-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bba68-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bba68-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bba68-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="bba68-110">Attributes</span></span>  
  
|<span data-ttu-id="bba68-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="bba68-111">Attribute</span></span>|<span data-ttu-id="bba68-112">Description</span><span class="sxs-lookup"><span data-stu-id="bba68-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bba68-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="bba68-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bba68-114">Spécifie que l’application intercepte les échecs d’exception d’État, tels que les violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="bba68-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bba68-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="bba68-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bba68-116">valeur</span><span class="sxs-lookup"><span data-stu-id="bba68-116">Value</span></span>|<span data-ttu-id="bba68-117">Description</span><span class="sxs-lookup"><span data-stu-id="bba68-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bba68-118">L’application n’intercepte pas les échecs d’exception d’État endommagés, tels que les violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="bba68-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="bba68-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bba68-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="bba68-120">L’application intercepte les échecs d’exception d’État, tels que les violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="bba68-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bba68-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bba68-121">Child Elements</span></span>  
 <span data-ttu-id="bba68-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="bba68-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bba68-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bba68-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bba68-124">Élément</span><span class="sxs-lookup"><span data-stu-id="bba68-124">Element</span></span>|<span data-ttu-id="bba68-125">Description</span><span class="sxs-lookup"><span data-stu-id="bba68-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bba68-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bba68-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bba68-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="bba68-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bba68-128">Notes</span><span class="sxs-lookup"><span data-stu-id="bba68-128">Remarks</span></span>  
 <span data-ttu-id="bba68-129">Dans la .NET Framework version 3,5 et les versions antérieures, le common language runtime permettait au code managé d’intercepter les exceptions levées par des États de processus endommagés.</span><span class="sxs-lookup"><span data-stu-id="bba68-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="bba68-130">Une violation d’accès est un exemple de ce type d’exception.</span><span class="sxs-lookup"><span data-stu-id="bba68-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="bba68-131">À partir du .NET Framework 4, le code managé n’intercepte plus ces types d’exceptions dans les blocs `catch`.</span><span class="sxs-lookup"><span data-stu-id="bba68-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="bba68-132">Toutefois, vous pouvez remplacer cette modification et maintenir la gestion des exceptions d’état endommagé de deux manières :</span><span class="sxs-lookup"><span data-stu-id="bba68-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="bba68-133">Affectez à l’attribut `enabled` de l’élément `<legacyCorruptedStateExceptionsPolicy>` la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="bba68-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="bba68-134">Ce paramètre de configuration est appliqué échelle et affecte toutes les méthodes.</span><span class="sxs-lookup"><span data-stu-id="bba68-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="bba68-135">ou</span><span class="sxs-lookup"><span data-stu-id="bba68-135">-or-</span></span>  
  
- <span data-ttu-id="bba68-136">Appliquez l’attribut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> à la méthode qui contient le bloc `catch` exceptions.</span><span class="sxs-lookup"><span data-stu-id="bba68-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="bba68-137">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bba68-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bba68-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="bba68-138">Example</span></span>  
 <span data-ttu-id="bba68-139">L’exemple suivant montre comment spécifier que l’application doit rétablir le comportement avant le .NET Framework 4 et intercepter tous les échecs d’exception d’état endommagé.</span><span class="sxs-lookup"><span data-stu-id="bba68-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bba68-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bba68-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="bba68-141">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="bba68-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bba68-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="bba68-142">Configuration File Schema</span></span>](../index.md)
