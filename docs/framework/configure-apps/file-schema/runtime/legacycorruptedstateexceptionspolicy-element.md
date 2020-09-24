---
title: Élément <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: f36e27a1b85cff2ba8c7e838bace37890a5aa760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151205"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="3cdb4-102">Élément \<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="3cdb4-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>

<span data-ttu-id="3cdb4-103">Spécifie si le common language runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="3cdb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cdb4-104">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cdb4-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3cdb4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3cdb4-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cdb4-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="3cdb4-107">Attributes</span></span>  
  
|<span data-ttu-id="3cdb4-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="3cdb4-108">Attribute</span></span>|<span data-ttu-id="3cdb4-109">Description</span><span class="sxs-lookup"><span data-stu-id="3cdb4-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3cdb4-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="3cdb4-111">Spécifie que l’application intercepte les échecs d’exception d’État, tels que les violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-111">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3cdb4-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="3cdb4-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="3cdb4-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="3cdb4-113">Value</span></span>|<span data-ttu-id="3cdb4-114">Description</span><span class="sxs-lookup"><span data-stu-id="3cdb4-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3cdb4-115">L’application n’intercepte pas les échecs d’exception d’État endommagés, tels que les violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-115">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="3cdb4-116">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3cdb4-117">L’application intercepte les échecs d’exception d’État, tels que les violations d’accès.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-117">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cdb4-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3cdb4-118">Child Elements</span></span>  

 <span data-ttu-id="3cdb4-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cdb4-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3cdb4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3cdb4-121">Élément</span><span class="sxs-lookup"><span data-stu-id="3cdb4-121">Element</span></span>|<span data-ttu-id="3cdb4-122">Description</span><span class="sxs-lookup"><span data-stu-id="3cdb4-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3cdb4-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3cdb4-124">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cdb4-125">Notes</span><span class="sxs-lookup"><span data-stu-id="3cdb4-125">Remarks</span></span>  

 <span data-ttu-id="3cdb4-126">Dans la .NET Framework version 3,5 et les versions antérieures, le common language runtime permettait au code managé d’intercepter les exceptions levées par des États de processus endommagés.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-126">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="3cdb4-127">Une violation d’accès est un exemple de ce type d’exception.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-127">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="3cdb4-128">À partir du .NET Framework 4, le code managé n’intercepte plus ces types d’exceptions dans des `catch` blocs.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-128">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="3cdb4-129">Toutefois, vous pouvez remplacer cette modification et maintenir la gestion des exceptions d’état endommagé de deux manières :</span><span class="sxs-lookup"><span data-stu-id="3cdb4-129">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="3cdb4-130">Affectez `<legacyCorruptedStateExceptionsPolicy>` à l’attribut de l’élément la valeur `enabled` `true` .</span><span class="sxs-lookup"><span data-stu-id="3cdb4-130">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="3cdb4-131">Ce paramètre de configuration est appliqué échelle et affecte toutes les méthodes.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-131">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="3cdb4-132">- ou -</span><span class="sxs-lookup"><span data-stu-id="3cdb4-132">-or-</span></span>  
  
- <span data-ttu-id="3cdb4-133">Appliquez l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribut à la méthode qui contient le `catch` bloc exceptions.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-133">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="3cdb4-134">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-134">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cdb4-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="3cdb4-135">Example</span></span>  

 <span data-ttu-id="3cdb4-136">L’exemple suivant montre comment spécifier que l’application doit rétablir le comportement avant le .NET Framework 4 et intercepter tous les échecs d’exception d’état endommagé.</span><span class="sxs-lookup"><span data-stu-id="3cdb4-136">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cdb4-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cdb4-137">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="3cdb4-138">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="3cdb4-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3cdb4-139">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="3cdb4-139">Configuration File Schema</span></span>](../index.md)
